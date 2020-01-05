<template>
   <tr>
     <td>{{item.employee_name}}</td>
     <td>{{item.employee_name }}</td>
     <td>{{item.employee_age}}</td>
     <!-- <button @click="viewItem">view</button> -->
     <button @click="editItem">edit</button>
      <button@click="deleteItem">delete</button@click="deleteItem">
    </tr>
</template>
<script>
export default {
    name:'Delete',
    props: {
        item:Object
    },
    methods:{
       deleteItem() {
      this.$http
        .delete(`http://dummy.restapiexample.com/api/v1/delete/${this.item.id}`)
        .then(response => {
          alert("list Deleted Successfully");
          console.log(response);
          this.$emit("reload");
        })
        .catch(error => {
          alert("Error Deleting list");
          alert(error.response);
        });
     
    
},
    editItem() {
      this.$router.push({ name: "edit-list", params: { id: this.item.id } });
    },
   
}
}
</script>