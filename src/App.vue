<template>
  <div id="app">
    <sidebar></sidebar>
    <todo></todo>
  </div>
</template>

<script>
import Todo from './components/Todo'
import Sidebar from './components/Sidebar'

export default {
  name: 'App',
  components: {
    Todo,
    Sidebar
  }
}
</script>

<style>
#app {
  font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
