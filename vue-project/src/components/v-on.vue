<script setup>
import { ref } from 'vue'

const counter = ref(0)

// 事件處理與表單綁定 v-on
const addHandler = (e) => {
	console.log(e);

	counter.value < 10 ? counter.value++ : counter.value = 0
}

const test = (e) => {

	console.log(e.currentTarget);

}
const keyupHandler = (e) => {
	console.log("keyup:", e);

}
const ctrlHandler = (e) => {
	console.log("ctrlHandler", e);

}
const ctrlaltHandler = (e) => {
	console.log("ctrlaltHandler", e);

}
// 表單綁定輸入 v-model
const message = ref('')
const check = ref(["A"])
const oneCheck = ref("A")
const selected = ref('')
const arraySelect = ref([])
const options = ref([
	{ text: 'One', value: 'A' },
	{ text: 'Two', value: 'B' },
	{ text: 'Three', value: 'C' }
])
const checked = ref("yes")
</script>

<!-- 學習影片: https://www.youtube.com/watch?v=8CVYizbi3Wk&t=377s -->
<!-- 官方文件: https://cn.vuejs.org/guide/essentials/event-handling.html -->
<template>
	<div class="greetings">
		<h3>
			事件處理與表單綁定 v-on
		</h3>
		<p>內聯事件處理</p>
		<button @click="counter < 10 ? counter++ : counter = 0">Add 1</button>
		<h3>函式方法處理(推薦)</h3>
		<p>參數的傳遞 ($event) </p>
		<button @click="addHandler($event)">Add 1</button>
		<button @click="addHandler">Add 1</button>
		<p>The button above has been clicked {{ counter }} times.</p>
		<h3>事件修飾符</h3>
		<p>prevent (防止)</p>
		<button @click.right.prevent="addHandler">@click.right.prevent</button>
		<div @click="test">
			1
			<div @click="test">
				2
				<div @click="test">
					3
					<a href="www.google.com" target="_blank" @click.stop="test">
						button
					</a>
					<input @keyup.ctrl.alt.exact="keyupHandler" placeholder="@keyup.ctrl.alt.exact" />
					<input @keydown.ctrl.c.exact="ctrlHandler" placeholder="@keydown.ctrl.c.exact" />
					<input @keydown.ctrl.alt.a.exact="ctrlaltHandler" placeholder="@keydown.ctrl.alt.a.exact" />
				</div>
			</div>
		</div>
		<h3>表單輸入綁定 v-model</h3>
		<p>Message is: {{ message }}</p>
		<!-- v-model 不會更新拼音中符號 -->
		<input :value="message" @input="e => message = e.target.value" />
		<input v-model="message" placeholder="v-model" />
		<!-- 
		錯誤 <textarea >{{ text }}</textarea>
		正確 <textarea v-model="text"></textarea>  
		-->
		<br />
		<p>多選 {{ check }}</p>
		<input type="checkbox" value="A" v-model="check"> A
		<input type="checkbox" value="B" v-model="check"> B
		<p>單選 {{ oneCheck }}</p>
		<input type="radio" value="A" v-model="oneCheck"> A
		<input type="radio" value="B" v-model="oneCheck"> B
		<p>Selected: {{ selected }}</p>
		<select v-model="selected">
			<!-- 依需求決定要不要 disabled -->
			<option disabled value="">請選擇</option>
			<option>A</option>
			<option>B</option>
			<option>C</option>
		</select>
		<p>arraySelect: {{ arraySelect }}</p>
		<template v-for="item of options" :key="item.value">
			<input v-model="arraySelect" :value="item.value" type="checkbox" />{{ item.text }}
		</template>
		<select v-model="arraySelect" multiple >
			<option v-for="item of options" :value="item.value" :key="item.value">{{ item.text }}</option>
		</select>
		<br />
		<input type="checkbox" id="checkbox" v-model="checked" true-value="yes" false-value="no" />
		<label for="checkbox">{{ checked }}</label>
	</div>
</template>

<style scoped>
select[multiple] {
	width: 100px;
}

h3 {
	font-size: 1.4rem;
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
