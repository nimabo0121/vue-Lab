<script setup>
import { ref } from 'vue'

const counter = ref(0)

const addHandler = (e) =>{
	console.log(e);
	
counter.value < 10 ? counter.value++ : counter.value = 0
}
</script>

<!-- 學習影片: https://www.youtube.com/watch?v=8CVYizbi3Wk&t=377s -->
<!-- 官方文件: https://cn.vuejs.org/guide/essentials/event-handling.html -->
<template>
	<p>內連事件處理</p>
	<button @click="counter < 10 ? counter++ : counter = 0">Add 1</button>
	<h3>函式方法處理(推薦)</h3>
	<p>參數的傳遞 (e) </p>
	<button @click="addHandler()">Add 1</button>
	<button @click="addHandler">Add 1</button>
	<p>The button above has been clicked {{ counter }} times.</p>
</template>