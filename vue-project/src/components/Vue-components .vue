<script setup>
import { ref } from 'vue';
import MyComp from './MyComp.vue';

const msg = ref('Hello World')

const props = {
    greetingMessage: "123",
    obj: {
        count: 1
    }
}


</script>

<template>
    <div class="greetings">
        <h1>組件註冊、屬性與事件</h1>
        <a href="https://vuejs.org/guide/components/registration.html">vue-components</a>
        <h2>{{ msg }}</h2>
        <input v-model="msg" />
        <!-- <br /> -->
        <!-- <MyComp greetingMessage="123" />  -->
        <!-- <br /> -->
        <!-- 官方建議使用 kebab-case -->
        <!-- <MyComp greeting-message="456" />  -->
        <br />
        <h3>使用 v-bind</h3>
        <a href="https://vuejs.org/guide/components/props.html">props</a>
        <MyComp v-bind="props" />
        <br />
        <MyComp greeting-message="456" :obj="props.obj" />
        <br />
        <img src="/src/assets/7.png" alt="" />

        <h1>prop 校驗</h1>
        <img src="/src/assets/8.png" alt="">
        <!-- <br /> -->
        <img src="/src/assets/9.png" alt="">
        <img src="/src/assets/10.png" alt="">
        <br />
        <p style="text-align: center;">validator 範例</p>
        <p> 自定義校驗函數, 這邊function寫在子元件中,<span style="color: red;">
                校驗父元件傳入參數 count 大於 5 </span>
        </p>
        <MyComp greeting-message="456" :obj="{ count: 4 }" />


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
