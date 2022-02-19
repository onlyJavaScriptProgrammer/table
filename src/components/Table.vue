<template>
  <div class="wrap">
    <button @click="addColumn">Add column</button>
    <button @click="delColumn">Delete column</button>
    <table>
      <thead>
        <tr>
          <th>#</th>
          <table-head
            v-for="(column, index) in columnsHead"
            :key="column.content"
            :content="column.content"
            :index="index"
            @edDataHead="saveDataHead"
          />
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(row, rowIndex) in rows"
          :key="row.rowId"
          @edData="saveData"
        >
          <td>{{rowIndex + 1}}</td>
          <table-body
            v-for="(column, index) in columnsBody"
            :key="column.content"
            :content="column.content"
            :index="index"
            :rowIndex="rowIndex"
          />
        </tr>
      </tbody>
    </table>
    <button @click="addRow">Add row</button>
    <button @click="delRow">Delete row</button>
  </div>
</template>

<script>
import TableHead from './TableHead.vue'
import TableBody from './TableBody.vue'

export default {
  name: 'Table',
  components: {
    TableHead,
    TableBody
  },
  data () {
    return {
      columnsHead: [
        {columnId: 1, content: 'Surname'},
        {columnId: 2, content: 'Name'},
        {columnId: 3, content: 'Second name'}
      ],
      columnsBody: [
        {columnId: 1, content: 'Ivanov'},
        {columnId: 2, content: 'Ivan'},
        {columnId: 3, content: 'Ivanovich'}
      ],
      rows: [
        {rowId: 1, content: 'Ivanov'},
        {rowId: 2, content: 'Ivan'},
        {rowId: 3, content: 'Ivanovich'}
      ]
    }
  },
  methods: {
    addColumn () {
      this.columnsBody.push({columnId: this.columnsBody.length + 1, content: 'data' + this.columnsBody.length})
      this.columnsHead.push({columnId: this.columnsBody.length + 1, content: 'data' + this.columnsBody.length})
    },
    addRow () {
      this.rows.push({rowId: this.rows.length + 1, content: ''})
    },
    delRow () {
      this.rows.pop()
    },
    delColumn () {
      this.columnsBody.pop()
      this.columnsHead.pop()
    },
    saveData (data, i, r) {
      this.columnsBody[i].content = data
    },
    saveDataHead (data, i) {
      this.columnsHead[i].content = data
    }
  }
}
</script>

<style>
table {
  border-collapse: collapse;
  margin: 10px 0;
}
td{
  border: 1px solid #000;
  padding: 5px;
}
th{
  background: #ccc;
  border: 1px solid #000;
  padding: 5px;
  font-weight: 400;
}
</style>
