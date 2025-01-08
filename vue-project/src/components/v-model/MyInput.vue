<script setup>
// import { ref } from 'vue'
defineProps(['modelValue'])
defineEmits(['update:modelValue'])



</script>

<template>
    <div class="greetings">
        <input 
        :value="modelValue" 
        @input="$emit('update:modelValue', $event.target.value)" />

    </div>

</template>

<style>
button,
a {
    display: block;
    margin-bottom: lem;
}

.greetings h1,
.greetings h3 {
    text-align: center;
}

@media (min-width: 1024px) {

    .greetings h1,
    .greetings h3 {
        text-align: center;
    }
}
</style>
