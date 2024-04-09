<template>
  <center>
    <img src="../assets/resto.webp" class="logo" alt="">
    <h1>Sign Up</h1>

    <div class="registation">
      <input v-model="name" type="text" name="name"  placeholder="Enter Name"><br /><br />
      <input v-model="email" type="text" name="email"  placeholder="Enter Email"><br /><br />
      <input v-model="password" type="password" name="password"  placeholder="Enter Password"><br /><br />
      <button type="button" v-on:click="signup">Sign in</button>
      <p>
        <router-link to="/login">Login</router-link>
      </p>
    </div>
  </center>
</template>

<script>
import axios from "axios"
export default {
  name: 'Signup',
  data() {
    return {
      name: '',
      email: '',
      password: ''
    }
  },
  methods: {
    async signup() {
      console.log("clicked", this.name, this.email)
      let results = await axios.post("http://localhost:3000/user", {
        email: this.email,
        name: this.name,
        password: this.password
      })
      console.warn(results);
        if (results.status === 201) {
        localStorage.setItem("userInfo", JSON.stringify(results.data))
        this.$router.push({
          name: "Home"
        })
      }
    }
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


