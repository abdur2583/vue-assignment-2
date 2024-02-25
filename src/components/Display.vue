<template>
    <div class="display">
      <span>{{ currentNumber }}</span>
      <span v-if="result">{{ result }}</span>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      currentNumber: String,
      result: String,
    },
  };
  </script>
  
  <style scoped>
    /* Add styling for display alignment and formatting */
  </style>