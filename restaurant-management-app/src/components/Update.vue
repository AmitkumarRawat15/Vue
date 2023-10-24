<template>
  <Header />
  <img class="logo" src="../assets/restarauntlogo.png">
  <h1>Update Restaurant</h1>
  <div class="update">
    <input type="Name" v-model="Restaurants.Name" placeholder="Enter Restaurant Name" />
    <input type="Address" v-model="Restaurants.Address" placeholder="Enter Restaurant Address" />
    <input type="Contact" v-model="Restaurants.Contact" placeholder="Enter Restaurant Contact" />
    <button v-on:click="UpdateRestaurant">Update Restaurant</button>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './Header.vue';
export default {
  name: 'UpdateRestaurant',
  components: {
    Header
  },
  data() {
    return {
      Restaurants: {
        Name: "",
        Address: "",
        Contact: ""
      }
    }
  },
  methods: {
    async UpdateRestaurant() {
      console.log(this.Restaurants)
      let response = await axios.put("http://localhost:3000/Restaurants/" + this.$route.params.id,
        {
          Name: this.Restaurants.Name,
          Address: this.Restaurants.Address,
          Contact: this.Restaurants.Contact
        })
      console.log(response)
      if (response.status == 200) {
        this.$router.push({ name: 'Home' })
      }

    }
  },
  async mounted() {
    let response = localStorage.getItem("details")

    if (!response) {
      this.$router.push({ name: 'SignUp' })
    }
    else {
      this.Name = JSON.parse(response).Name
    }
    let result = await axios.get("http://localhost:3000/Restaurants/" + this.$route.params.id)
    console.log(result.data)
    this.Restaurants = result.data
  }
}

</script>

