<template>
  <div class="about">
    <h1>This is an about page</h1>
    <table>
      <thead>
        <tr>
          <th>employee-name</th>
          <th>employee-salary</th>
          <th>employee-age</th>
         </tr>
        <Del v-for="list in tableList" :key="list.id" @reload="restart()" :item="list"></Del>
      </thead>
      <tbody>
        
      </tbody>
    </table>

  </div>
</template>
<script>
import Del from '@/components/del.vue'
export default{
  name:'About',
  components:{
    Del
  },
  data(){
    return {
      tableList:[]
    }
  },
  methods: {
    restart(){
      this.$http.get('http://dummy.restapiexample.com/api/v1/employees')
       .then(response => {
          this.tableList = response.data
        })
        .catch(error=>{
          console.log(error.response)
        })
    },
  },
 mounted(){
   this.restart()
 }
};

</script>
<style scoped>
table {
  border: 1px solid black;
  width: 100%;
}
td, th {
  border: 1px solid #3333;
  padding: 1rem;
}
tr:nth-child(even) {
background:pink;
}
button {
  width:100px;
  padding: 20px;
  border-radius:none; 
  color:black;
  background:pink;
  font-size:14px;
}
</style>