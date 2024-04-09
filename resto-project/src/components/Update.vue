<template>
  <Header />
  <center>
    <h1>Update Restaurant</h1>
    <form class="add">
      <input type="text" v-model="restaurant.name" name="name" id="name" placeholder="Enter Name"><br><br>
      <input type="text" v-model="restaurant.address" name="address" id="address" placeholder="Enter Address"><br><br>
      <input type="text" v-model="restaurant.contact" name="contact" id="contact" placeholder="Enter Contact"><br><br>
      <button type="button" v-on:click=updateRestaurant>Update Restaurant</button>
    </form>
  </center>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue"
export default {
  name: "Update ",
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
  methods: {
    async updateRestaurant() {
      const results = await axios.put("http://localhost:3000/restaurant/" + this.$route.params.id, {
        name: this.restaurant.name,
        address: this.restaurant.address,
        contact: this.restaurant.contact
      });
      if (results.status === 200) {
        this.$router.push({
          name: "Home"
        })
      }
    }
  },
  async mounted() {
    let user = localStorage.getItem('userInfo');
    if (!user) {
      this.$router.push({
        name: "Signup"
      })
    }
    const results = await axios.get("http://localhost:3000/restaurant/" + this.$route.params.id)
    console.warn(results)
    // console.warn(this.$route.params.id)
    this.restaurant = results.data
  }
}
</script>
