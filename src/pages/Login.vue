<template>
    <SiteNavigation :msg="guest"></SiteNavigation>
    <div class="min-h-screen flex items-center justify-center">
        <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" @submit.prevent="handleLogin">
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-bold mb-2"> Username </label>
                <input v-model="username" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="text" placeholder="Type here">
            </div>
            <div class="mb-6">
                <label class="block text-gray-700 text-sm font-bold mb-2" >Password</label>
                <input v-model="password" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="password" placeholder="Type here">
            </div>
            <div class="flex items-center justify-between">
                <button class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit">Login</button>
            </div>
        </form>
    </div>
</template>

<script setup lang="ts">
import { Ref, ref } from 'vue'
import SiteNavigation from '../components/SiteNavigation.vue';
import userData from '../assets/users.json'

const username : Ref<string> = ref('')
const password : Ref<string> = ref('')
const guest : Ref<string> = ref('')

function handleLogin() {
    const user = userData.find(data => data.username === username.value);
    if (user && user.password === password.value) {
    console.log('Authentication successful');
    guest.value = username.value;
  } else {
    console.log('Authentication failed');
  }
}

</script>

<style lang="scss" scoped>

</style>