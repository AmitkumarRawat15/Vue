<template>
    <img class="logo" src="../assets/restarauntlogo.png">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" v-model="Name" placeholder="Enter Name" />
        <input type="text" v-model="Email" placeholder="Enter Email" />
        <input type="password" v-model="Password" placeholder="Enter Password" />
        <button v-on:click="SignUp">Sign Up</button>
        <p>
            <router-link to="/Login">Login</router-link>
        </p>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'SignUp',
    data() {
        return {
            Name: "",
            Email: "",
            Password: "",
        }
    },
    methods: {
        async SignUp() {
            let result = await axios.post("http://localhost:3000/users",
                {
                    Name: this.Name,
                    Email: this.Email,
                    Password: this.Password,
                })
            console.log(result)
            if (result.status == 201) {
                localStorage.setItem("details", JSON.stringify(result.data))
                this.$router.push({ name: 'Home' })
            }

        }
    },
    mounted() {
        let response = localStorage.getItem("details")
        if (response) {
            this.$router.push({ name: 'Home' })
        }
    }
}
</script>
