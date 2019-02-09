<template>
  <div id="app">
    <total-cost></total-cost>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import TotalCost from './components/TotalCost'

export default {
  name: 'App',
  components: {
    TotalCost
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
}
</style>
