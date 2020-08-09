<template>
  <div>
      <form @submit.prevent="register">
        <label for="name">
            Name:    
        </label> 
        <input type="text" v-model="name" />
        <label for="name">
            Email:    
        </label> 
        <input type="email" v-model="email" />
        <label for="password">
            Password:    
        </label> 
        <input type="password" v-model="password" />

        <button type="submit" name="butoon">Register</button>
    </form>    
        <router-link to="/login">Have an account? Login</router-link>
  </div>
</template>

<script>
export default {
    data() {
        return {
            name: '',
            email: '',
            password: ''
        }
    },
    methods: {
        register() {
            this.$store.dispatch('register', {
                name: this.name,
                email: this.email,
                password: this.password
            })
            .then( () => {
                this.$router.push({ name: 'dashboard'})
            })
        }
    }
}
</script>

<style scoped>

</style>