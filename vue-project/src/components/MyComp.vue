<script setup>
import { ref } from 'vue';


const props = defineProps({
    greetingMessage:{
        type: String,
        required:true
    },
    obj:{
        type: Object,
        required:true,
        validator:(value)=>{
            return value.count < 5
        }
    }
});

const count = ref(props.obj.count)

</script>

<template>
    {{ props.greetingMessage }}
    {{ count }}
    <button @click="count++">
        change
        </button>
</template>
