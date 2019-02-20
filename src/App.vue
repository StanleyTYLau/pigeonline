<template>
  <div id="app">
    <img alt="Pigeonline logo" src="./assets/pigeonline.png">
    <ChartVis v-bind:userData = "userData" v-bind:testing = "testing"/>
    <TableData v-bind:userData = "userData"/>
    
  </div>
</template>

<script>
import json from './assets/data.json'
import TableData from './components/Table.vue'
import ChartVis from './components/Chart.vue'

export default {
  name: 'app',
  components: {
   TableData,
   ChartVis
  },
  data() {
    return {
      userData: json,
      testing: "some text"
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
