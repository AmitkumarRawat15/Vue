<template>
    <div class="topnav">
        <router-link to="/">Home</router-link>
        <router-link to="/Add">Add Restaurant</router-link>
        <a v-on:click="logout" href="#">Logout</a>
        <div class="loggeduser">
            Logged user : {{ Name }}
        </div>
    </div>
</template>

<script>
export default {
    name: "HeaderMenu",
    data() {
        return {
            Name: ""
        }
    },
    methods: {
        logout() {
            localStorage.clear();
            this.$router.push({ name: 'Login' })
        }
    },
    mounted() {
        let response = localStorage.getItem("details")

        if (!response) {
            this.$router.push({ name: 'SignUp' })
        }
        else {
            this.Name = JSON.parse(response).Name
        }

    }
}
</script>
