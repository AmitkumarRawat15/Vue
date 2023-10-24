<template>
  <Header />
  <!-- <h1>Welcome {{ Name }} to the home page</h1> -->
  <h1>Home page</h1>
  <table border="1px">
    <tr>
      <th>
        Restaurants Name
      </th>
      <th>
        Restaurants Address
      </th>
      <th>
        Restaurants Contact
      </th>
      <th>
        Actions
      </th>
    </tr>
    <tr v-for="items in Restaurants" :key="items.id">
      <td>{{ items.Name }}</td>
      <td>{{ items.Address }}</td>
      <td>{{ items.Contact }}</td>
      <td><router-link :to="'/Update/' + items.id"><img class="edit" src="../assets/pencil.png"></router-link>
        <img v-on:click="deleteRestaurant(items.id)" class="delete" src="../assets/delete.png">
      </td>
    </tr>
  </table>
</template>

<script>
import axios from 'axios';
import Header from './Header.vue';
export default {
  name: 'HomePage',
  components: {
    Header
  },
  data() {
    return {
      Name: "",
      "Restaurants": []
    }
  },
  methods: {
    async deleteRestaurant(id) {
      let result = await axios.delete("http://localhost:3000/Restaurants/" + id)
      if (result.status == 200) {
          this.loadData()
      }
    },
    async loadData() {
      let response = localStorage.getItem("details")

      if (!response) {
        this.$router.push({ name: 'SignUp' })
      }
      else {
        this.Name = JSON.parse(response).Name
      }
      let result = await axios.get("http://localhost:3000/Restaurants")
      this.Restaurants = result.data
    }
  },
  mounted() {
    this.loadData()
  }
}
</script>

