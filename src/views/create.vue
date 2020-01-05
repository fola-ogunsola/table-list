<template>
  <div class="about">
    <h1>Add to list</h1>
    <div class="form_item">
      <form @submit.prevent="submitName">
        <div class="form_item">
          <label for="name">Name</label>
          <input type="text" name="name" placeholder="e.g kofo" v-model="addList.employee_name">
        </div>
        <div class="form_item">
          <label for="type">salary</label>
          <input  name="number" v-model="addList.employee_salary" >
        
        </div>
        <div class="form_item">
          <label for="age">Age</label>
          <input type="number" name="age" placeholder="1" v-model="addList.employee_age">
        </div>
        <button class="form_button" type="submit">
          Submit
        </button>
      </form>
  </div>

  </div>
</template>
<script>
export default {
  name: 'createList',
  data() {
    return {
      addList: {
        employee_name: '',
        employee_salary: '',
        employee_age: ''
      }
    }
  },
  methods: {
    submitName() {
      this.$http.post('http://dummy.restapiexample.com/api/v1/create', this.addList)
        .then(response => {
          this.addList = {
             employee_name: '',
            employee_salary: '',
             employee_age: ''
          }
          alert(`Successfully added item with id ${response.data.id}`)
        })
        .catch(error => {
          alert(error.response)
        })
    }
  }
}
</script>
<style scoped>
.form_item {
  display: block;
  max-width: 100%;
  margin-bottom: 1rem;
}
.form_item > label {
  display: block;
}
.form_item > input {
  padding: 1rem;
  font-size: 18px;
  border-radius: 8px;
  color: pink;
  background: #fff;
  border: 2px solid pink;
  width: 90%;
}
.form_button {
  width: 100px;
  color: black;
  background-color: aqua;
}
</style>