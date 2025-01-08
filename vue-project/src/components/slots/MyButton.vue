<script setup>
defineProps(['iconSrc', 'text'])
</script>
<template>
    <button>
        <template v-if="iconSrc">
            {{ iconSrc }}
        </template>
        {{ text }}
    </button>
</template>
<style>

</style>