<template>
<Header />
<center>
  <h1>{{ name }}'s Home Component</h1>
  <table border="1">

    <tr>
      <td>Id</td>
      <td>Name</td>
      <td>Address</td>
      <td>Contact</td>
      <td>Action</td>
    </tr>
    <tr v-for="item in restaurants" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.address }}</td>
      <td>{{ item.contact }}</td>
      <td>
        <router-link :to="'/update/' + item.id">Update</router-link>
        <button v-on:click="deleteRestaurant(item.id)">Delete</button>
      </td>
    </tr>
  </table>
</center>
</template>

<script>
import axios from "axios";
import Header from "./Header.vue"
export default {
  name: "Home",
  data() {
    return {
      name: '',
      restaurants: [],
    }
  },
  methods: {
    async deleteRestaurant(id) {
      let results = await axios.delete("http://localhost:3000/restaurant/" + id);
      if (results.status == 200) {
this.loadData()
      }
    },
    async loadData() {

      let user = localStorage.getItem('userInfo');
      this.name = JSON.parse(user).name
      if (!user) {
        this.$router.push({
          name: "Signup"
        })
      }
      let results = await axios.get("http://localhost:3000/restaurant")
      this.restaurants = results.data
    }
  },

  components: {
    Header
  },
  async mounted() {
this.loadData();
  },

}
</script>

<style>
td {
  width: 85px;
  text-align: center
}
</style>
