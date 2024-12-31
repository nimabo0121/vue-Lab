<script setup>
import { computed, reactive, ref, watch, onMounted } from 'vue';

// ------------watch 範例------------
const msg = ref("Hello World")

watch(msg, () => {
    console.log("change");

})

// ------------偵聽資料來源類型------------
const A = ref(1)
const B = ref(1)

const c = computed(() => {
    return A.value + B.value
})

// 第一種

// watch(A, ()=>{
//     console.log("change");
// })


// 第二種... 可watch function
watch(() => A.value + B.value, (newValue, oldValue) => {
    console.log("change1", newValue, oldValue);
})
// change1 13 2

// 第三種... 陣列型
watch([A, B], (newValue, oldValue) => {
    console.log("change2", newValue, oldValue);
})

//change2 > (2) [12, 1] > (2) [1, 1]

// 直接偵聽c , A,B 改變都會更改c
watch(c, (newValue, oldValue) => {
    console.log("change3", newValue, oldValue);
})

// change3 13 2

// watch 不能偵聽響應是對象的屬性值 -- reactive 的內容, 但可以將整個watch, 但會變成深層偵聽器 
const obj = reactive({ count: 0 })

// 錯誤, 因為watch() 得到的參數是一個 number
// watch(obj.count, (count) => {
//     console.log(`Count is: $(count)`);
// })

// 正確做法: 傳回該屬性的 getter 函數
watch(
    () => obj.count, (count) => {
        console.log(`Count is: ${count}`);
    }
)

// 深層偵聽器: 直接給watch()傳入一個響應式對象，會隱式地建立一個深層偵聽器－該回呼函數在所有嵌套的變更時都會被觸發：

// 等於偵聽整個物件
const obj1 = reactive({ count: 0 })

watch(obj1, (newValue, oldValue) => {
    console.log("change4", newValue, oldValue);
})
// 在嵌套的属性变更时触发
// 注意：`newValue` 此处和 `oldValue` 是相等的
// 因为它们是同一个对象！

// 即時回呼的偵聽器 immediate: true
const obj2 = reactive({ count: 0 })

watch(obj1, (newValue, oldValue) => {
    console.log("change5--immediate", newValue, oldValue);
}, { immediate: true })

// 模板引用
const lastInput = ref(null)
console.log("lastInput:", lastInput.value);
onMounted(() => {
    console.log("astInput-onMounted():", lastInput.value);
}) // onMounted 之後才拿得到

// 訪問模板引用
const focusInput = ref(null)
console.log("focusInput:", focusInput.value)
onMounted(() => {
    focusInput.value.focus();

})

// 函數模板引用
function refHandler(el){
    if(el) el.focus();
}

</script>

<template>
    <div class="greetings">
        <h1>生命週期掛鉤</h1>
        <h3>computed與watch 差異</h3>
        <p>computed : 計算屬性允許我們聲明性地計算衍生值。</p>
        <p>watch : 我們需要在狀態變化時執行一些「副作用」：例如更改DOM，或根據非同步操作的結果去修改另一處的狀態。</p>
        <br />
        <h3>~~ watch 範例 ~~</h3>
        <p>資料變動時,觸發function</p>
        <h2>{{ msg }}</h2>
        <input v-model="msg">
        <h3>偵聽資料來源類型</h3>
        <p>watch的第一個參數可以是不同形式的「資料來源」：它可以是一個ref (包括計算屬性)、一個響應式物件、一個getter 函數、或多個資料來源組成的陣列</p>

        <input v-model.number="A">
        +
        <input v-model.number="B">
        =
        <input v-model="c">

        <h3>深層偵聽器--範例 Change4</h3>
        <input v-model="obj1.count">
        <p>會導致newValue, oldValue值相同</p>

        <h3>即時回呼的偵聽器</h3>
        <p>watch預設是懶執行的：只有當資料來源變化時，才會執行回呼。</p>
        <p>但在某些場景中，我們希望在建立偵聽器時，立即執行一遍回呼。</p>
        <p>我們可以透過傳入immediate: true選項來強制偵聽器的回呼立即執行。</p>
        <input v-model="obj2.count">
        <h3>~~ WatchEffect ~~</h3>
        <div>
            <a href="https://cn.vuejs.org/guide/essentials/watchers.html">Vue偵聽器文件</a>
            <img src="/src/assets/1.png" alt="">
            <img src="/src/assets/2.png" alt="">
            <img src="/src/assets/3.png" alt="">
            <img src="/src/assets/4.png" alt="">
            <img src="/src/assets/5.png" alt="">
        </div>

        <h3>模板引用</h3>
        <a href="https://cn.vuejs.org/guide/essentials/template-refs.html">Vue模板引用文件</a>
        <img src="/src/assets/6.png" alt="">
        <h4>範例</h4>
        <input ref="lastInput" />
        <h3>訪問模板引用</h3>
        <input ref="focusInput" />
        <h3>函數模板引用</h3>
        <input :ref="refHandler" />
        

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