<template>
  <Header />
  <center>
    <h1>Add New Restaurant</h1>
    <form class="add">
      <input type="text" v-model="restaurant.name" name="name" id="name" placeholder="Enter Name"><br><br>
      <input type="text" v-model="restaurant.address" name="address" id="address" placeholder="Enter Address"><br><br>
      <input type="text" v-model="restaurant.contact" name="contact" id="contact" placeholder="Enter Contact"><br><br>
      <button type="button" v-on:click=addRestaurant>Add New Restaurant</button>
    </form>
  </center>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue"
export default {
  name: "Add",
  components: {
    Header
  },
  data() {
    return {
      restaurant: {
        name: "",
        address: "",
        contact: ""
      }
    }
  },

  mounted() {
    let user = localStorage.getItem('userInfo');
    if (!user) {
      this.$router.push({
        name: "Signup"
      })
    }
  },
  methods: {
    async addRestaurant() {
      console.warn(this.restaurant)
      const results = await axios.post("http://localhost:3000/restaurant", {
        name: this.restaurant.name,
        address: this.restaurant.address,
        contact: this.restaurant.contact
      });
      if (results.status === 201) {
        this.$router.push({
          name: "Home"
        })
      }
    }
  }

}
</script>

<style></style>
