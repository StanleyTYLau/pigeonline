
<script>

import { Bar, mixins} from 'vue-chartjs'

const { reactiveProp } = mixins

export default {
  name: "ChartVis",
  extends: Bar,
  mixins: [reactiveProp],
  data() {
    let newOptions = {
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

    return {
      options: newOptions
    }
  },
  
  mounted() {
    //this.chartData created by mixin
    this.renderChart(this.chartData, this.options);
    
  }
}
</script>

<style>

</style>
