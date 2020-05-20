<template>
  <v-content id="app">
    <router-view />
  </v-content>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    //
  })
};
</script>


<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  min-height: 100vh;
  /* background-color: #E9E9F0; */
  /* background-color: #f0f0f7; */
}
</style>