<template>
  <div>
    <h4>Chart {{abc}}</h4>
  </div>
</template>

<script>
export default {
  name: "ChartVis",
  props: ["userData", "testing"],
  data() {
    const gmailRegEx = /gmail/gi
    const yahooRegEx = /yahoo/gi
    const aolRegEx = /aol/gi
    let countGmail = 0
    let countYahoo = 0
    let countAol = 0
    
    for (let user in this.userData){
      //console.log(this.userData[user].email)
      if((this.userData[user].email).indexOf("gmail")) {
        countGmail += 1
      }
      else if (yahooRegEx.test(this.userData[user].email)) {
        countYahoo += 1
      }
      else if (aolRegEx.test(this.userData[user].email)) {
        countAol += 1
      }
    }

    return {
      abc: this.testing + " hello!Gmail: " + countGmail + " Yahoo:" + countYahoo + " Aol:" + countAol
    }
  }
}
</script>

<style>

</style>
