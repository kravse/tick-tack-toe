<template>
  <div id="app">
    <h1>tick tack toe</h1>
    <board msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import board from './components/board.vue'

export default {
  name: 'app',
  components: {
    board
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
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
