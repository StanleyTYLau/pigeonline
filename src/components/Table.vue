<template>
  <div>
    <h1>User Data</h1>
    <h3>Please confirm the 'Email' and 'Province' columns by selecting the table header</h3>
    <table id="table1"> 
      <thead>
        <tr>
          <th nowrap><b-button :pressed.sync="toggle1" variant="primary" v-on:click="checkEmailProv()">First Name</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle2" variant="primary" v-on:click="checkEmailProv()">Last Name</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle3" variant="primary" v-on:click="checkEmailProv()">Company</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle4" variant="primary" v-on:click="checkEmailProv()">Address</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle5" variant="primary" v-on:click="checkEmailProv()">City</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle6" variant="primary" v-on:click="checkEmailProv()">Province</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle7" variant="primary" v-on:click="checkEmailProv()">Postal Code</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle8" variant="primary" v-on:click="checkEmailProv()">Phone# 1</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle9" variant="primary" v-on:click="checkEmailProv()">Phone# 2</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle10" variant="primary" v-on:click="checkEmailProv()">Email</b-button></th>
          <th nowrap><b-button :pressed.sync="toggle11" variant="primary" v-on:click="checkEmailProv()">Web</b-button></th>
        </tr>
      </thead>

      <tbody>
        <tr v-bind:key="user.phone1 + user.phone2"  v-for="user in userData">
          <td>{{user.first_name}}</td>
          <td>{{user.last_name}}</td>
          <td>{{user.company_name}}</td>
          <td>{{user.address}}</td>
          <td>{{user.city}}</td>
          <td>{{user.province}}</td>
          <td>{{user.postal}}</td>
          <td>{{user.phone1}}</td>
          <td>{{user.phone2}}</td>
          <td>{{user.email}}</td>
          <td>{{user.web}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "TableData",
  props: ["userData"],
  data() {
    return {
      toggle1: false,
      toggle2: false,
      toggle3: false,
      toggle4: false,
      toggle5: false,
      toggle6: false,
      toggle7: false,
      toggle8: false,
      toggle9: false,
      toggle10: false,
      toggle11: false,
    }
  },
  methods: {
    checkEmailProv() {
      if (this.toggle6 && this.toggle10 && !this.toggle1 && !this.toggle2 && !this.toggle3 && 
      !this.toggle4 && !this.toggle5 && !this.toggle7 && !this.toggle8 && !this.toggle9 && !this.toggle11){
        this.$emit('show', true);
      }
    }
  }
}
</script>

<style>
table {
  font-family: 'Open Sans', sans-serif;
  width: 750px;
  border-collapse: collapse;
  border: 3px solid #44475C;
  margin: 10px 10px 0 10px;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475C;
  color: #FFF;
  padding: 8px;
  min-width: 30px;
}

table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7D82A8;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #D4D8F9;
}
</style>
