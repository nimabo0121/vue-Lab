<script setup>
import { computed } from 'vue';

// import { ref } from 'vue'
const props = defineProps(['modelValue'])
const emit = defineEmits(['update:modelValue'])

const value = computed({
    get() {
        return props.modelValue
    },
    set(value) {
        emit('update:modelValue', value)
    }
})

</script>

<template>
    <div class="greetings">
       
        <input v-model="value" />
        <button @click="value++">
            Add
        </button>
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
