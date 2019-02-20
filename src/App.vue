<template>
  <div id="app">
    <img alt="Pigeonline logo" src="./assets/pigeonline.png">
    <TableData v-bind:userData = "userData"/>
    
  </div>
</template>

<script>
import json from './assets/data.json'
import TableData from './components/Table.vue'

export default {
  name: 'app',
  components: {
   TableData
  },
  data() {
    return {
      userData: json
    }
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
