<script setup>
import { ref } from 'vue'
const apiResponse = ref([])
function fetchJokes() {
    fetch('https://animechan.xyz/api/random')
    .then(response => response.json())
    .then(data => (apiResponse.value = data))
}
</script>

<template>
  <div style="text-align: left;">
    <div class="hello">
		<h1>Random Value </h1>
    <p>ID: {{ apiResponse.id }}</p>
    <p>Quote: {{ apiResponse.quote }}</p>
    <p>anime: {{ apiResponse.quote }}</p>
    <p>character: {{ apiResponse.quote }}</p>
		<button @click="fetchJokes()">Click Me To Get Values</button>
	</div>
</div>
</template>

<style scoped>
  .hello {
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    width: 100%;
  }
</style>
