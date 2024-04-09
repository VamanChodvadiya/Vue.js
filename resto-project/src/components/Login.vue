<template>
  <center>
    <img src="../assets/resto.webp" class="logo" alt="">
    <h1>Login</h1>

    <div class="login">
      <input v-model="email" type="text" name="email" placeholder="Enter Email"><br /><br />
      <input v-model="password" type="password" name="password" placeholder="Enter Password"><br /><br />
      <button type="button" v-on:click="login()">Login</button>
      <p>
        <router-link to="/signup">Sign up</router-link>
      </p>
    </div>
  </center>
</template>

<script>
import axios from 'axios';
export default {
  name: "Login",
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    async login() {
      let results = await axios.get(
        `http://localhost:3000/user?email=${this.email}&password=${this.password}`
      )
      console.warn(results)
      if (results.status === 200 && results.data.length > 0) {
        localStorage.setItem("userInfo", JSON.stringify(results.data[0]))
        this.$router.push({
          name: "Home"
        })
      }
    },

  },
  mounted() {
    let user = localStorage.getItem('userInfo');
    if (user) {
      this.$router.push({
        name: "Home"
      })
    }
  }
}
</script>
<style>
.login {
  border: 1px solid;
  margin: 19px;
  border-bottom-left-radius: 39px;
  border-top-left-radius: 39px;
  border-bottom-right-radius: 39px;
  border-top-right-radius: 39px;
  padding: 9px;
  width: 226px;
  border-style: outset;
  border-block-end-width: 7px;
}
</style>
