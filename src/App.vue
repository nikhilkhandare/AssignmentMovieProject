<template>
  <div id="app">
   <HelloWorld />
   <!-- <Movies /> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// import Movies from './components/Movies.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    // Movies
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
