<template>
  <div id="app">
    <HelloWorld msg="Welcome to The Infinity War"/>
         <player/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import player from './components/player'

export default {
  name: 'App',
  components: {
    HelloWorld,
    player,
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
