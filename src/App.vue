<template>
  <div id="app">
    <img id="logo" alt="Pigeonline logo" src="./assets/pigeonline.png">
      
    <div id="chart">
      <ChartParent v-bind:userData = "userData" v-if="showChart"/>
    </div>
    
    <TableData v-bind:userData = "userData" v-on:show="toggleShow()"/>
    
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
      userData: json,
      showChart: false,
    }
  },
  methods: {
    toggleShow() {
      this.showChart = true
    }
  }
}
</script>

<style>
#logo {
  margin-bottom: 20px;
}

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
  margin: 0 auto 25px auto;
}
</style>
