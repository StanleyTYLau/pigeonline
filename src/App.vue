<template>
  <div id="app">
    <img alt="Pigeonline logo" src="./assets/pigeonline.png">
      
    <div id="chart">
      <ChartParent v-bind:userData = "userData" />
    </div>
    
    <TableData v-bind:userData = "userData"/>
    
  </div>
</template>

<script>
import json from './assets/data.json'
import TableData from './components/Table.vue'
import ChartParent from './components/ChartParent.vue'

export default {
  name: 'app',
  components: {
   TableData,
   ChartParent
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

#chart {
  width: 60%;
  margin: 0 auto;
}
</style>
