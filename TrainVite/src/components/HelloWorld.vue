<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios';

defineProps<{ msg: string }>()

const message = ref('')
const count = ref(0)
const list = ref([])
const getList = async function () {
  const { data } = await axios.get("http://gorest.co.in/public/v2/todos")
  list.value = data
}
</script>

<template>
  <div class="grid grid-cols-3 my-10"></div>
  <div class="col-start-2"></div>
  <h1 class="text center">{{ msg + ' ' + message}}</h1>
  <pre>{{ list }}</pre>
  <div class="card text-center"></div>
    <div v-for="(item,index) in list" :key="index"></div>
    <div class="border-gray-200 bg-white px-10 py-10 text-start my-10 rounded-xl"></div>
    <input type="text" v-model="message" />
    <button type="button" @click="getList()">GET LIST </button>
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
 

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>