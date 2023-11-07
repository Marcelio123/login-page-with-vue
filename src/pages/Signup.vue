<template>
    <SiteNavigation></SiteNavigation>
    <div>
        <form @submit.prevent="handleSubmit">
            <div>
                <label> First Name </label>
                <input v-model="firstName" placeholder="Type here">
            </div>
            <div>
                <label> Last Name </label>
                <input v-model="lastName" placeholder="Type here">
            </div>
            <div>
                <label> Username </label>
                <input v-model="username" placeholder="Type here">
            </div>
            <div>
                <label> Password </label>
                <input v-model="password" placeholder="Type here">
            </div>
            <div>
                <button>Sign in</button>
            </div>
        </form>
    </div>
    <div>
        <p>{{ username }}</p>
        <p>{{ password }}</p>
    </div>
</template>

<script setup lang="ts">
import SiteNavigation from '../components/SiteNavigation.vue';
import { Ref, ref } from 'vue'
import fs from "fs";

const filePath = '../assets/uers.json';
const firstName : Ref<string> = ref('')
const lastName : Ref<string> = ref('')
const username : Ref<string> = ref('')
const password : Ref<string> = ref('')

function handleSubmit() {
    // Read the existing JSON data from the file
    const jsonData = JSON.parse(fs.readFileSync(filePath, 'utf8'));
    const newData = {
        "username": username.value,
        "password": password.value,
        "firstName": firstName.value,
        "lastName": lastName.value
    }
    // Append newData to the existing data array
    jsonData.push(newData);
    // Write the updated data back to the file
    fs.writeFileSync(filePath, JSON.stringify(jsonData, null, 2));
    console.log('success')
}

</script>

<style lang="scss" scoped>

</style>