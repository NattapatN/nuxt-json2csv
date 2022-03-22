<template>
  <div class="container pt-5"> 
    <div class="row pt-5">
      <div class="center pointer" @click="downloadCsv()">
        <button type="button" class="btn btn-success">Download CSV</button>
        <img src="~assets/image/csv-icon.png" alt="" style="width: 30px;">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  methods:{
    downloadCsv(){
      console.log("download csv")
    }
  }
}
</script>

<style scoped>
.center {
  margin: auto;
}
.pointer {
  cursor: pointer;
}
</style>
