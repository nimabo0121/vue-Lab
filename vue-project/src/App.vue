<script setup>
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import vOn from './components/v-on.vue';
import HelloVue from './components/Hello-vue.vue';
import onMounted from './components/on-mounted.vue';
const visibilityState  = ref({
  vOn: false,
  HelloVue: false,
  onMounted: false,
})

const toggleVisibility = (key) => {
  visibilityState.value[key] = !visibilityState.value[key]
}

function getButtonText(key) {
  return visibilityState.value[key] ? '一' : '十'
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />
    <div class="wrapper">
      <HelloWorld msg="Sam's Vue-Lab !" />
    </div>
  </header>

  <main>
    <button @click="toggleVisibility('vOn')">
      事件處理與表單綁定 v-on {{ getButtonText('vOn') }}
    </button>
    <vOn v-if="visibilityState.vOn" />
    <button @click="toggleVisibility('HelloVue')">
      Vue 基礎範例 {{ getButtonText('HelloVue') }}
    </button>
    <HelloVue v-if="visibilityState.HelloVue" />
    <button @click="toggleVisibility('onMounted')">
      生命週期、偵聽器、模板引用 {{ getButtonText('onMounted') }}
    </button>
    <onMounted v-if="visibilityState.onMounted" />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}

button {
  display: block;
  margin: 1rem auto;
  padding: 0.5rem 1rem;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #358a63;
  
}

h3 {
	font-size: 1.4rem;
}

</style>
