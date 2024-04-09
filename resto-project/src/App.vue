<template>
  <router-view></router-view>
</template>
<script>
import Signup from "./components/Signup.vue"
export default {
  name: 'App',
  components: {
    Signup
  }

}
</script>

<style>
.logo {
  width: 87px;
}

.registation {
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

.registation input,
.login input,
.add input {
  margin-right: auto;
  margin-left: auto;
  border: 1px solid lightblue;
  width: 170px;
  font-size: small;
}

.registation button,
.login button,
.add button {
  border: 1px solid lightblue;
  background-color: lightblue;
  width: 170px;
  cursor: pointer;
}

.nav {
  background-color: black;
  padding: 5px;
}

.nav a {
  color: white;
  margin: 5px;
  font-size: small;
}

.nav a:hover {
  background-color: #777;
  color: white;
  padding: 5 px;
}
</style>
