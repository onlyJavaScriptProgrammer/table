<template>
  <div id="app">
    <div class="container">
      <Table/>
    </div>
  </div>
</template>

<script>
import Table from './components/Table.vue'

export default {
  name: 'App',
  components: {
    Table
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.container{
  width: 1200px;
  margin: 0 auto;
  padding: 20px 0;
  display: flex;
}
</style>
