<template>
  <div id="app">
    <img class="logo" src="./assets/logo.png" />
    <RandomCat msg="Random Gif Cat" />
  </div>
</template>

<script>
import RandomCat from './components/RandomCat.vue'

export default {
  name: 'App',
    data() {
      return {};
    },

  components: {
    RandomCat
  }
}
</script>

<style>
body {
  background-color: black;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px auto;
  background-color: lightblue;
  width: 550px;
  height: 900px;
}

.logo {
  margin-top: 20px;
  width: 100px;
}

</style>
