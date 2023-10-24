<template>
    <img class="logo" src="../assets/restarauntlogo.png">
    <h1>Login</h1>
    <div class="login">
        <input type="text" v-model="Email" placeholder="Enter Email" />
        <input type="password" v-model="Password" placeholder="Enter Password" />
        <button v-on:click="Login">Login</button>
        <p>
            <router-link to="/SignUp">SignUp</router-link>
        </p>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'LoginPage',
    data() {
        return {
            Email: "",
            Password: ""
        }
    },
    methods: {
        async Login() {
            let result = await axios.get(`http://localhost:3000/users?Email=${this.Email}&Password=${this.Password}`)
            if (result.status == 200 && result.data.length > 0) {
                localStorage.setItem("details", JSON.stringify(result.data[0]))
                this.$router.push({ name: 'Home' })
            }
            else{
                alert("Enter correct Email and Password")
                this.Email = ''
                this.Password = ''
            }

        }

    },
    mounted(){
        let response = localStorage.getItem("details")
        if (response){
            this.$router.push({name:'Home'})
        }
    }
}
</script>
