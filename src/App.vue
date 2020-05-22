<template>
  <div id="app">
    <!-- <img src="./assets/logo.png" class="logo"> -->
    <todolist />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import todolist from './components/todolist'

export default {
  name: 'App',
  components: {
    HelloWorld,
    todolist
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 100%;
}
</style>
