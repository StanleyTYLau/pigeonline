<template>

  <div id="chart">
    <span>Filter by province: </span>
    <select v-model="provSelect" v-on:change="changeProv()">
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
    <span>Selected: {{ provSelect }}</span>
    
    <ChartVis v-bind:data = "chartData" />
  </div>
   
</template>

<script>
import ChartVis from './Chart.vue'

export default {
  name: 'ChartParent',
  components: {
   ChartVis
  },
  props: ["userData"],
  created() {
    this.changeProv()
  },
  data() {
    
    return {
      provSelect: 'All Provinces',
      chartData: {},
    }
  },
  methods: {
    changeProv() {
      const gmailRegEx = /gmail/i
      const yahooRegEx = /yahoo.com/i
      const aolRegEx = /aol/i
      let countGmail = 0
      let countYahoo = 0
      let countAol = 0
      let total = 0
      let prov = this.provSelect
      
      //iterate thru json userData and count emails
      for (let user in this.userData){
        if (this.userData[user].province == prov || prov == "All Provinces"){
          total += 1
          let email = this.userData[user].email

          if(gmailRegEx.test(email)) {
            countGmail += 1
          }
          else if (yahooRegEx.test(email)) {
            countYahoo += 1
          }
          else if (aolRegEx.test(email)) {
            countAol += 1
          }
        }
      }
      this.chartData = {
        labels: ["Gmail", "Yahoo", "AOL", "Other"],
        datasets: [
          {
            label: "Number of Emails Types",
            data: [countGmail, countYahoo, countAol, (total - countGmail - countYahoo - countAol)],
            backgroundColor: [
              'rgba(71, 183,132,.5)', // Green
              'rgba(71, 183,132,.5)', // Green
              'rgba(71, 183,132,.5)', // Green
              'rgba(71, 183,132,.5)' // Green
            ],
            borderColor: [
              '#47b784',
              '#47b784',
              '#47b784',
              '#47b784'
            ],
            borderWidth: 3
          }
        ] 
      }

    }
  } 
}
</script>

<style>

</style>
