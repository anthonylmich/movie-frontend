<script>
import axios from "axios";

export default {
  data: function () {
    return {
      newUserParams: { name: "", password: "" },
      errors: [],
    };
  },
  methods: {
    submit: function () {
      axios
        .post("/users", this.newUserParams)
        .then((response) => {
          console.log(response.data);
          this.$router.push("/login");
        })
        .catch((error) => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>

<template>
  <div class="signup">
    <form v-on:submit.prevent="submit()">
      <h1>Signup</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Name:</label>
        <input type="text" v-model="newUserParams.name" /><br />
        <small>{{ 25 - newUserParams.name.length }} characters remaining</small>
      </div>
      <div>
        <label>Email:</label>
        <input type="email" v-model="newUserParams.email" />
      </div>
      <div>
        <label>Password:</label>
        <input type="password" v-model="newUserParams.password" /><br />
        <small class="Issues" v-if="newUserParams.password.length < 8">must be at least 8 characters long</small>
        <small class="Issues" v-if="newUserParams.password.length > 20"> Cannot be longer than 20 characters</small>
      </div>
      <div>
        <label>Password confirmation:</label>
        <input type="password" v-model="newUserParams.password_confirmation" /><br />
        <small class="issues" v-if="newUserParams.password !== newUserParams.password_confirmation && newUserParams.password.length > 0">
        Password confirmation must match password</small>
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<style scoped>
.issues {
  color: rgb(198, 6, 6);
}
</style>
