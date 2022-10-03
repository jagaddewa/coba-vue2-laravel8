<template>
    <div>
      <div class="container">
        <h2>Add Student</h2>
        <div class="panel panel-primary">
          <div class="panel-heading">
              Add Student
              <router-link to="/" class="btn btn-info pull-right" style="margin-top:-7px;margin-left:2px;">Student List</router-link>
          </div>
          <div class="panel-body">
            <form @submit.prevent="addStudent">
              <div class="form-group">
                <label>Name</label>
                <input type="text" class="form-control" v-model="student.name" />
              </div>
              <div class="form-group">
                <label>Address</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="student.address"
                />
              </div>
              <button type="submit" class="btn btn-primary">Add</button>
            </form>
          </div>
        </div>
      </div>
    </div>
  </template>
   
  <script>
  export default {
    data() {
      return {
        student: {},
      };
    },
    methods: {
      addStudent() {
        this.axios
          .post("http://localhost:9292/api/students", this.student)
          .then((response) => this.$router.push({ name: "home" }))
          .catch((err) => console.log(err))
          .finally(() => (this.loading = false));
      },
    },
  };
  </script>
  