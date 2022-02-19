<template>
  <td >
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
  </td>
</template>

<script>
export default {
  name: 'table-body',
  props: {
    rowIndex: Number,
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
      this.$emit('edData', this.contentValue, this.index, this.rowIndex)
    }
  }
}
</script>

<style scoped>
td{
  border: 1px solid #000;
  padding: 5px;
}
span {
  cursor: pointer;
}
</style>
