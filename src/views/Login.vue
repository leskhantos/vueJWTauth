<template>
    <div>
    <form @submit.prevent="login">
        <label>
            Email:
        </label>
        <input v-model="email" type="email" name="email" value>

        <label>
            Password:
        </label>
        <input v-model="password" type="password" name="password" value>
        <p>{{ error }}</p>

        <button type="submit" name="button">
            Login
        </button>

        <router-link to="/register">
            Don't have an account? Register.
        </router-link>
    </form>
    </div>
</template>

<script>
    export default {
        name: "Login",
        data () {
            return {
                email: '',
                password: '',
                error:null
            }
        },
        methods: {
            login () {
                this.$store
                    .dispatch('login', {
                        email: this.email,
                        password: this.password
                    })
                    .then(() => { this.$router.push({ name: 'dashboard' }) })
                .catch(err => {
                        this.error = err.response.data.error
                    })
            }
        }
    }
</script>

<style scoped>

</style>