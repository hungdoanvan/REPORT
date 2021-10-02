<template>
  <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> 
    <!-- <test/> -->
    <!-- <realtime-data/> -->
  </div>
</template>

<script>
// import RealtimeData from './components/realtimeData.vue'
import HelloWorld from './components/HelloWorld.vue'
// import Test from './components/test.vue'

export default {
  name: 'App',
  components: {
    // RealtimeData,
    HelloWorld,
    // Test,

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
  margin-top: 60px;
}
</style>
