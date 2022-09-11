<template>
    <form class="p-10 w-2/3" @submit="login">
        <input v-model="email" type="email" name="email" class="w-full px-4 py-3 my-2 rounded-lg border border-black shadow-sm focus:shadow-outline text-gray-600" placeholder="Email" />
        <input v-model="password" type="password" name="password" class="w-full px-4 py-3 my-2 rounded-lg border border-black shadow-sm focus:shadow-outline text-gray-600" placeholder="password" />

        <button type="submit" class="w-32 focus:outline-none border border-transparent py-2 px-5 rounded-lg shadow-sm text-center text-white bg-blue-500 hover:bg-blue-600 font-medium">Login</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
        }
    },
    methods: {
        async login(e) {
            e.preventDefault()

            const payload = {
                email: this.email,
                password: this.password,
            }

            try {
                const response = await this.$auth.loginWith('local', {
                    data: payload,
                })
                this.$auth.setUser(response.data.data.user)
                this.$router.push('/')
            } catch (e) {
                this.$router.push('/login')
            }
        },
    },
}
</script>
