
<script>
import Chart from 'chart.js'
import { Bar, mixins} from 'vue-chartjs'

const { reactiveData } = mixins

export default {
  name: "ChartVis",
  extends: Bar,
  props: ["userData", "testing"],
  mixins: [reactiveData],
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

    let chartOptions = {
      responsive: true,
      lineTension: 1,
      scales: {
        yAxes: [{
          ticks: {
            beginAtZero: true,
            padding: 25,
            stepSize: 100,
          }
        }]
      }      
    }
    
    return {
      abc: this.testing + " hello!Gmail: " + countGmail + " Yahoo:" + countYahoo + " Aol:" + countAol,
      chartData: chartData,
      chartOptions: chartOptions,
      provinceFilter: ''
    }
  },

  mounted() {
    this.renderChart(this.chartData, this.chartOptions);

  }
}
</script>

<style>

</style>
