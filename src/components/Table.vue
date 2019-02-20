<template>
  <div>
    <h1>Table</h1>

    <table id="table1"> 
      <thead>
        <tr>
          <th>first_name</th>
          <th>last_name</th>
          <th>company_name</th>
          <th>address</th>
          <th>city</th>
          <th>province</th>
          <th>postal</th>
          <th>phone1</th>
          <th>phone2</th>
          <th>email</th>
          <th>web</th>
        </tr>
      </thead>

      <tbody>
        <tr v-bind:key="user.postal" v-for="user in userData">
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
  props: ["userData"]
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
