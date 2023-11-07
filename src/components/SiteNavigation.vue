<template>
    <header class="sticky top-0 bg-white shadow-lg">
        <nav class="flex flex-row justify-between items-center gap-4 py-6 px-20">
            <p class="text-2xl">
                My Website
            </p>
            <div v-if="msg === ''" class="flex flex-row ">
                <router-link to="/login" class="text-green-500 hover:underline">Log in</router-link>
                <span class="mx-2"> | </span>
                <router-link to="/signup" class="text-green-500 hover:underline">Sign In</router-link>
            </div>
            <div v-else class="text-2xl text-green-500">
                {{ msg }}
            </div>
        </nav>
    </header>
</template>

<script setup lang="ts">
import { Ref, ref } from 'vue'

const userExist : Ref<boolean> = ref(false)

const props = defineProps({
  msg: String
})



</script>

<style lang="scss" scoped>

</style>
