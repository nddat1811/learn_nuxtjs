<template>
  <form  @submit.prevent="submitLogin">
    <div class="container">
      <input type="text" placeholder="Enter Username" name="uname" v-model="username" required />

      <input type="password" placeholder="Enter Password" name="psw" v-model="password" required />

      <button type="submit">Login</button>
    </div>

    <div class="container" style="background-color: #f1f1f1">
      <button type="button" class="cancelbtn">Cancel</button>
      <span class="psw">Forgot <a href="#">password?</a></span>
    </div>
  </form>
</template>

<script>
import axios from 'axios';
import { onMounted, ref } from 'vue';

export default {
  data() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    async submitLogin() {
      console.log("sokjadoadskoasdkasd")
      const username = this.username;
      const password = this.password;
      const result = await axios.post(`http://localhost:8090/login`, {
        username,
        password
      });
      console.log(result)
      if (result.data){
        this.$router.push('/')
      }
    }
  }
};
</script>

<style>

</style>