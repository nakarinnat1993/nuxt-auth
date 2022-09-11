<template>
    <div class="container text-center">
        <h1 class="m-2 text-xl">NUXT AUTH</h1>

        <div v-if="loggedIn">
            <h1 class="text-md">Hello, {{ user.email }}</h1>
            <button @click="logout" class="w-32 focus:outline-none border border-transparent py-2 px-5 rounded-lg shadow-sm text-center text-white bg-red-500 hover:bg-red-600 font-medium">Logout</button>
        </div>

        <div v-else>
            <nuxt-link to="/login" class="w-32 focus:outline-none border border-transparent py-2 px-5 rounded-lg shadow-sm text-center text-white bg-blue-500 hover:bg-blue-600 font-medium">Login</nuxt-link>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            user: this.$auth.user,
            loggedIn: this.$auth.loggedIn,
        }
    },
    methods: {
        async logout() {
            await this.$auth.logout()
            this.$router.push('/login')
        },
    },
}
</script>

<style>
</style>
