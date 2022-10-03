<template>
    <div>
      <div class="container">
        <h2>Update Student</h2>
        <div class="panel panel-primary">
          <div class="panel-heading">
              Update Student
              <router-link to="/" class="btn btn-info pull-right" style="margin-top:-7px;margin-left:2px;">Student List</router-link>
          </div>
          <div class="panel-body">
            <form @submit.prevent="updateStudent">
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
  
              <button type="submit" class="btn btn-primary">Update</button>
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
    created() {
      this.axios
        .get(`http://localhost:9292/api/students/${this.$route.params.id}`)
        .then((res) => {
          this.student = res.data;
        });
    },
    methods: {
      updateStudent() {
        this.axios
          .patch(
            `http://localhost:9292/api/students/${this.$route.params.id}`,
            this.student
          )
          .then((res) => {
            this.$router.push({ name: "home" });
          });
      },
    },
  };
  </script>
             