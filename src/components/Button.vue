<template>
    <button :class="{ active: value === operator }" @click="$emit('click', value)">{{ value }}</button>
  </template>
  
  <script>
  export default {
    props: {
      value: String,
      operator: String, // Pass from Calculator.vue
    },
  };
  </script>
  
  <style scoped>
    /* Add styling for buttons (size, colors) */
  </style>