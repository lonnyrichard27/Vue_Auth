<template>
  <div>
    <form @submit.prevent="login">
        <label for="email">
            Email:    
        </label> 
        <input type="text" v-model="email" />

        <label for="password">
            Password:    
        </label> 
        <input type="password" v-model="password" />

        <button type="submit" name="button">Login</button>
        <p>{{ error }}</p>

    <router-link to="/register">Dont have an account? Register</router-link>

    </form>    
  </div>
</template>

<script>
export default {
    data() {
        return{
            email: '',
            password: '',
            error: null
        }
    },
    methods: {
        login() {
            this.$store.dispatch('login', {
                email: this.email,
                password: this.password
            })
            .then(() => {
                this.$router.push({ name: 'dashboard'})
            })
            .catch((err) => {
                this.error = err.response.data
            })
        }
    }
}
</script>

<style>

</style>