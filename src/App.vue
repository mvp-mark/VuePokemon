<template>
  <div class="flex justify-center">
    <!--<img alt="Vue logo" src="./assets/logo.png" /> -->
    <div class="flex justify-center"></div>
    <HelloWorld msg="Os 151 Pokémon's" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
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
