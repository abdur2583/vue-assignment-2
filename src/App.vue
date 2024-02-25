<script setup>
import Calculator from './components/Calculator.vue'
import ApiData from "./components/ApiData.vue"
import Test from "./components/Test.vue"
</script>

<template>
  <Calculator/>
  <ApiData/>
  <Test/>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
