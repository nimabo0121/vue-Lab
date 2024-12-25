<script setup>
const props = defineProps({
    item: Object
})
</script>

<template>
    <li>{{ item.text }}</li>
</template>