<script setup>
import { computed } from 'vue'


const props = defineProps({
    firstName: String,
    lastName: String,
})
const emit = defineEmits([
    'updatea:firstName', 'update:lastName'
])

const firstName = computed({
    get() {
        return props.firstName
    },
    set(value) {
        emit('update:firstName', value)
    }
})

</script>
<template>
    <div class="greetings">
        <input type="text" v-model="firstName" />

        <input type="text" :value="lastName" @input="$emit('update:lastName',
            $event.target.value)" />

    </div>
</template>
<style>
button,
div a {
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