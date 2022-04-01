<template>
  <div class="container pt-5"> 
    <div class="row pt-5">
      <div class="col-6">
      <textarea v-text="data" rows="20" cols="50">
        
      </textarea>
      </div>
      <div class="center pointer" @click="exportCSV(data)">
        <button type="button" class="btn btn-success">Download CSV</button>
        <img src="~assets/image/csv-icon.png" alt="" style="width: 30px;">
      </div>
    </div>
  </div>
</template>

<script>
import { parseAsync } from 'json2csv'

export default {
  name: 'IndexPage',
  data() {
    return {
      data: {
        header: [
          {label: "No.", value: "no"},
          {label: "Firstname", value: "firstname"},
          {label: "Lastname", value: "lastname"}
        ],
        body: [
          {no: 1, firstname: "example1", lastname: "lastname1"},
          {no: 2, firstname: "example2", lastname: "lastname2"},
          {no: 3, firstname: "example3", lastname: "lastname3"},
        ]
      }
    }
  },
  methods:{
    async exportCSV(data){
      parseAsync(data.body, {
      fields: data.header,Headers: null
      }).then((csv) => {
        const csvContent = 'data:text/csvcharset=utf-8,\uFEFF' + encodeURI(csv)
        const link = document.createElement('a')
        link.setAttribute('href', csvContent)
        link.setAttribute('download', 'example.csv')
        link.click()
      }).catch(err => console.error(err))
    }
  }
}
</script>

<style scoped>
 textarea {
   resize: none;
 }
.pointer {
  cursor: pointer;
}
</style>
