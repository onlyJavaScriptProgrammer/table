<template>
  <th>
    <div
      @click="edit"
      v-if="!isClicked"
    >
      {{content}}
    </div>
    <div class="wrap_input" v-else>
    <input
      type="text"
      v-model="contentValue"
    />
    <span @click="close">&times;</span>
    </div>
  </th>
</template>

<script>
export default {
  name: 'table-head',
  props: {
    index: Number,
    content: Number | String
  },
  data () {
    return {
      isClicked: false,
      contentValue: this.content
    }
  },
  methods: {
    edit () {
      this.isClicked = !this.isClicked
    },
    close () {
      this.isClicked = false
      this.$emit('edDataHead', this.contentValue, this.index)
    }
  }
}
</script>

<style scoped>
th{
  background: #ccc;
  border: 1px solid #000;
  padding: 5px;
  font-weight: 400;
}
span {
  cursor: pointer;
}
</style>
