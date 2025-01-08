<script setup>
defineProps(['iconSrc', 'text'])
    const mtText = "AAA"
</script>
<template>
    <button>
        <template v-if="iconSrc">
            {{ iconSrc }}
        </template>
        {{ text }}
    <slot :text="mtText">
        Slot Default
    </slot>
    </button>
    
</template>
<style>
button{
    color: red;
    
}
</style>