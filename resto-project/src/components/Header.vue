<template>
  <div class="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/add">Add Restaurant</router-link>>
    <a v-on:click="logout()" href="#">LogOut</a>
  </div>
</template>
<script>
import router from '@/router';
export default {
  name: "Header",
  methods: {
    logout() {
      localStorage.clear()
      this.$router.push({ name: "Login" })
    }
  }
}
</script>