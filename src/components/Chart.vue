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
        arr.push(email)
      }
      else if (aolRegEx.test(email)) {
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
