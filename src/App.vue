<template>
  <div id="app">
    <HelloWorld msg="Welcome to The Infinity War" />
    <player />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import player from "./components/player";

export default {
  name: "App",
  components: {
    HelloWorld,
    player,
  },
};
</script>

<style>
#app {
  background-size: cover;
  background-image: url(https://i.pinimg.com/originals/8d/3a/de/8d3adebb383b640c8e8dba217bbbafe0.jpg);
  font-family: "Permanent Marker", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #646464;
}
</style>
