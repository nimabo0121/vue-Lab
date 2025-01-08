<script setup>
import FancyButton from './FancyButton.vue';
import MyButton from './MyButton.vue';
import SlotsPlural from './SlotsPlural.vue';
import SlotsReverse from './SlotsReverse.vue';

const text = "Click Me"

</script>
<template>
    <div class="greetings">
        <h1> Slots 與 依賴注入 </h1>
        <p>slots 適合使用在需要重複使用的情境</p>
        <button>
            Click <span>Me</span>
        </button>

        <MyButton iconSrc="!!!" :text="'Click Me'">

        </MyButton>

        <FancyButton />
        <FancyButton>
            Click me
        </FancyButton>
        <p>多個slots插槽內容, 要為具名插槽船入內容,需要一個含有 <span>v-slot</span>指令的 <span>template </span>元素。</p>
        <SlotsPlural>
            <template v-slot:icon>
                <img style="width: 20px;height: auto;"
                    src="C:\Users\Sam_Liu\Documents\Sam\vueLab\vue-project\src\assets\logo.svg" alt="">
            </template>
            <template #text>
                text !!! {{ text }}
            </template>
        </SlotsPlural>
        <p>反向傳遞</p>
        <SlotsReverse :text="text" iconSrc="!!!" v-slot="slotProps">
            {{ slotProps }}
        </SlotsReverse>
    </div>
</template>

<style>
p span {
    color: black;
    border: 2px solid red;
    padding: 0px 2px 0px 2px;
}

span,
p {
    font-weight: bold;
}

/*  */
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
