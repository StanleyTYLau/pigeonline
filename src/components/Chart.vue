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
    let somedata = this.testing
    return {
      abc: this.testing + " hello!"
    }
  }
}
</script>

<style>

</style>
