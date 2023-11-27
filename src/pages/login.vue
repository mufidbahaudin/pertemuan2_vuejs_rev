<script setup lang="ts">
    import { useAuthStore } from '@/stores/auth';
    import { ref } from 'vue';
    import axios from 'axios';
    import { useRouter } from 'vue-router';


    const auth = useAuthStore()
    const username = ref('')
    const password = ref('')
    const router = useRouter()

    const onLogin = async() => {
        const response = await axios ({
            method: 'post',
            url: 'http://localhost:3000/login',
            data: {
                username: username.value,
                password: password.value,
            }
    });

console.log(response)
    //     const validUsername = 'admin'
    //     const validPassword = 'admin'

    //     if (username.value === validUsername && password.value === validPassword) {
    //         auth.login(username.value)
    //         router.push('/')
    //     } else {
    //         window.alert('Login invalid')
    //     }
    // }

// function axios(arg0: { method: string; url: string; data: { firstName: string; lastName: string; }; }) {
// throw new Error('Function not implemented.');
}
</script>

<template>
    <div>
        <h1>Login Page</h1>
        <div class="flex flex-col gap-2">
            <input type="text" v-model="username" class="border p-2" placeholder="Username" />
            <input type="password" v-model="password" class="border p-2" placeholder="Password" />
            <button @click="onLogin" class="bg-blue-500 text-white py-1 px-3">Login</button>
        </div>
    </div>
</template>
