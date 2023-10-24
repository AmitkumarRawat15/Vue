<template>
  <router-view />
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.logo {
  width: 120px;
}

.edit,
.delete {
  width: 40px;
  margin-left: 10px;
  margin-left: 10px;
}

.register input,
.login input,
.add input,
.update input {
  width: 300px;
  height: 40px;
  display: block;
  margin-bottom: 20px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid moccasin;
  padding-left: 10px;
}

.topnav {
  background-color: slategray;
  overflow: hidden;
}

body {
  margin: 0;
  padding: 0;
}

.topnav a {
  color: snow;
  font-weight: bold;
  text-decoration: none;
  font-size: 15px;
  padding: 10px 10px;
  float: left;
}

.topnav .loggeduser{
  float: right;
  color: snow;
  font-weight: bold;
  font-size: 15px;
  padding: 10px 10px;
}

.register button,
.login button,
.add button,
.update button {
  width: 315px;
  height: 40px;
  border: 1px solid moccasin;
  background: moccasin;
  cursor: pointer;
}

table {
  margin-left: auto;
  margin-right: auto;
  border-collapse: collapse;
  width: 100%
}

th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: center;
  background-color: teal;
  color: white;
}

td {
  width: 200px;
  height: 50px;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: #ddd;
}
</style>
