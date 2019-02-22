

<template>
  <div>
    <h4>Chart {{abc}}</h4>
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

    <canvas id="email-chart"></canvas>
  </div>
</template>

<script>
import Chart from 'chart.js'

export default {
  name: "ChartVis",
  props: ["userData", "testing"],
  methods: {
    createChart(chartId, chartData) {
      const ctx = document.getElementById(chartId);
      const myChart = new Chart(ctx, {
        type: chartData.type,
        data: chartData.data,
        options: chartData.options,
      });
    }
  },

  data() {
    const gmailRegEx = /gmail/i
    const yahooRegEx = /yahoo.com/i
    const aolRegEx = /aol/i
    let countGmail = 0
    let countYahoo = 0
    let countAol = 0
    let total = 0
    
    //iterate thru json data and count emails
    for (let user in this.userData){
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

    //create data object for chart
    let chartData = {
      type: "bar",
      data: {
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
      },
      options: {
        responsive: true,
        lineTension: 1,
        scales: {
          yAxes: [{
            ticks: {
              beginAtZero: true,
              padding: 25,
            }
          }]
        }
      }
    }
    
    return {
      abc: this.testing + " hello!Gmail: " + countGmail + " Yahoo:" + countYahoo + " Aol:" + countAol,
      chartData: chartData,
      provinceFilter: ''
    }
  },

  mounted() {
    this.createChart('email-chart', this.chartData);
  }
}
</script>

<style>

</style>
