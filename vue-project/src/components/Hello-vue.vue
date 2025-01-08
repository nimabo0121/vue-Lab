<script setup>
import { ref, computed } from "vue"

import TodoItem from "./TodoItem.vue"
import TodoList from "./TodoList.vue"
// 處理使用者輸入
const msg = ref("Hello World")// 原始資料


const isReverse = ref(false)

const displayMsg = computed(() => {

    if (isReverse.value) {
        return msg.value.split('').reverse().join('')
    } else {
        return msg.value
    }
})// 顯示資料

const reverseHandler = () => {

    isReverse.value = !isReverse.value
}

const appendHandler = () => {
    msg.value += '!'
}

const clickHandler = () => {
    alert("click")
}
// 屬性綁定
const title = ref("Hello")

const isRed = ref(true)
const toggleRed = () => {
    isRed.value = !isRed.value
}

const color = ref('green')
const toggleColor = () => {
    color.value = color.value === 'green' ? 'blue' : 'green'
}
// 條件和循環
const list = ref([1, 2, 3])

const show = ref(true)

const pushHandler = () => {
    list.value.push(list.value.length + 1)
}

const popHandler = () => {
    list.value.pop()
}
const showhiddenHandler = () => {
    show.value = !show.value
}
const reverse = () => {
    list.value.reverse()
}

// 表單綁定
const text = ref('Edit me')
const checked = ref(true)
const checkedNames = ref(['Jack'])
const picked = ref('One')
const selected = ref('')
// const multiSelected = ref(['A'])

// 組件simple-component
const groceryList = ref([
    { id: 0, text: 'Vegetables' },
    { id: 1, text: 'Cheese' },
    { id: 2, text: 'Whatever else humans are supposed to eat' }
])

</script>

<template>
    <div class="greetings">

        <h1>ex.1 處理使用者輸入 </h1>
        <h3>handling-input</h3>
        <!-- 示範使用 v-on 指令處理使用者輸入 -->
        <div>
            <h2>
                {{ displayMsg }}
            </h2>
            <!-- 綁定到方法/函數。
                @click 文法是 v-on:click 的縮寫。 -->
            <button @click="reverseHandler">
                Reverse
            </button>
            <button @click="appendHandler">
                Append
            </button>
            <!-- prevent常見修飾符 -->
            <a href="https://google.com" target="_blank" @click.prevent="clickHandler">
                A Link with preventDefault()
            </a>
        </div>
        <h1>ex.2 屬性綁定 </h1>
        <h3>attribute-bindings</h3>
        <!-- 將元素屬性/屬性反應性地綁定到狀態。 -->
        <div>
            <p>
                <!-- :title 語法是 v-bind:title 的縮寫。 -->
                <span :title="title">
                    將滑鼠懸停在我的上方幾秒鐘即可查看我的動態綁定標題！
                </span>
            </p>
            <!-- 類別綁定對物件和陣列有特殊支持
                除了普通字串之外 -->
            <p :class="{ red: isRed }" @click="toggleRed">
                This should be red... but click me to toggle it.
            </p>
            <!-- 樣式綁定也支援物件和數組 -->
            <p :style="{ color }" @click="toggleColor">
                This should be green, and should toggle between green and blue on click.
            </p>
        </div>
        <h1>ex.3 條件和循環 </h1>
        <h3>conditionals-and-loops</h3>
        <!-- 使用 v-if 和 v-for 指令有條件或循環地渲染內容。 -->
        <div>

            <p>
                <button @click="showhiddenHandler">
                    show / hide
                </button>
                <button @click="pushHandler">Push</button>
                <button @click="popHandler">pop</button>
                <button @click="reverse">reverse</button>
            </p>
            <ul v-if="show && list.length > 0">
                <li v-for="value of list" :key="value">
                    {{ value }}
                </li>
            </ul>
            <p v-else>
                hidden
            </p>
        </div>
        <h1>
            ex.4 表單綁定
        </h1>
        <h3>form-bindings</h3>
        <!-- 使用 v-model 指令在狀態和表單輸入之間建立雙向綁定。 -->
        <div>
            <h2>文字輸入</h2>
            <input v-model="text">
            <p>{{ text }}</p>

            <h2>Checkbox</h2>
            <input type="checkbox" id="checkbox" v-model="checked" true-value="Yes" false-value="No">
            <label for="checkbox">已檢查: {{ checked }}</label>


            <h2>單選</h2>
            <input type="radio" id="one" value="One" v-model="picked">
            <label for="one">One</label>
            <br>
            <input type="radio" id="two" value="Two" v-model="picked">
            <label for="two">Two</label>
            <p>Picked: {{ picked }}</p>

            <h2>選擇</h2>
            <select v-model="selected">
                <option disabled value="">請選擇一個</option>
                <option>A</option>
                <option>B</option>
                <option>C</option>
            </select>
            <p>已選擇: {{ selected }}</p>
            <!--多個複選框可以綁定到同一個數組 v 模型值-->
            <h2>多複選框</h2>
            <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
            <label for="jack">Jack</label>
            <input type="checkbox" id="john" value="John" v-model="checkedNames">
            <label for="john">John</label>
            <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
            <label for="mike">Mike</label>
            <p>已檢查姓名: {{ checkedNames }}</p>

            <h2>多選
            </h2>
            <select v-model="checkedNames" multiple style="width:100px">
                <option>Jack</option>
                <option>John</option>
                <option>Mike</option>
            </select>
            <p>已選擇: {{ checkedNames }}</p>

        </div>
        <h1>ex.5 組件</h1>
        <h3>simple-component</h3>
        <!-- 最簡單的元件，它接受一個 prop 並渲染它。 -->
        <!-- 我們為每個待辦事項提供待辦事項對象它具有代表性，因此它的內 容可以是動態的。我們還需要為每個組件提供一個“密鑰”，v-for 的指南部分對此進行了解釋。 -->
        <ul>
            <TodoItem v-for="item of groceryList" :item="item" :key="item.id" />
        </ul>
        <!-- 整包宣告成一個駔件 -->
        <TodoList :list="groceryList" />
    </div>
</template>

<style>
.red {
    color: red;
}

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