<script setup>
import { ref } from "vue"

import CustomInput from './CustomInput.vue';
import MyInput from "./MyInput.vue";
import MyCounter from "./MyCounter.vue";
import UserName from "./UserName.vue";

const message = ref("Hello")
const count = ref(0)

// 多個參數綁定-- 結合v-model 參數設定
const first = ref('John')
const last = ref('Doe')

</script>

<template>
    <div class="greetings">
        <h1>
            組件 V-model
        </h1>
        <a href="https://cn.vuejs.org/guide/components/v-model.html">v-model</a>
        <CustomInput v-model="message" /> {{ message }}
        <MyInput v-model="message" /> {{ message }}
        <br />
        <h3>使用 computed</h3>
        {{ count }}
        <br />
        <MyCounter v-model="count" />
        <h3>多個v-model 綁定</h3>
        <h4>寫法差異</h4>
        <p>first 使用computed, 可大幅度節省template 內容</p>
        <h4 style="">{{ first }}{{ last }}</h4>
        <UserName 
        v-model:first-name="first"
         v-model:last-name="last" />



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
