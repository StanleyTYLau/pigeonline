<template>
  <div id="app">
    <img alt="Pigeonline logo" src="./assets/pigeonline.png">
    <div>
      <span>Filter by province: </span>
      <select v-model="provinceFilter">
      <option disabled value="">Please select one</option>
      <option>All Provinces</option>
      <option>AB</option>
      <option>BC</option>
      <option>MB</option>
      <option>NB</option>
      <option>NL</option>
      <option>NT</option>
      <option>NS</option>
      <option>NU</option>
      <option>ON</option>
      <option>PE</option>
      <option>QC</option>
      <option>SK</option>
      <option>YT</option>
      </select>
      <span>Selected: {{ provinceFilter }}</span>
    </div>
   
    <div id="chart">
      <ChartVis v-bind:userData = "userData" v-bind:testing = "testing"/>
    </div>
    
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
      testing: "some text",
      provinceFilter: ''
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
