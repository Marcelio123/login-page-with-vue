<template>
    <div>
        {{ msg }}
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
  msg: String
})
</script>

<style lang="scss" scoped>

</style>