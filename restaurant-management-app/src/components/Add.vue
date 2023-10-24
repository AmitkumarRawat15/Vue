<template>
  <Header />
  <img class="logo" src="../assets/restarauntlogo.png">
  <h1>Add Restaurant</h1>
  <div class="add">
    <input type="Name" v-model="Name" placeholder="Enter Restaurant Name" />
    <input type="Address" v-model="Address" placeholder="Enter Restaurant Address" />
    <input type="Contact" v-model="Contact" placeholder="Enter Restaurant Contact" />
    <button v-on:click="Addrestaurant">Add Restaurant</button>
  </div>
</template>

<script>
import axios from 'axios'
import Header from './Header.vue';
export default {
  name: 'AddRestaurant',
  components: {
    Header
  },
  methods: {
    async Addrestaurant() {
      let result = await axios.post("http://localhost:3000/Restaurants",
        {
          Name: this.Name,
          Address: this.Address,
          Contact: this.Contact,
        })

      if (result.status == 201) {
        this.$router.push({ name: 'Home' })
      }
      else{
        alert("something went wrong please try again!!!")
      }

    }
  }
}
</script>

