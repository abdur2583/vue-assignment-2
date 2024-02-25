<script>
import { ref } from 'vue'
import Display from './Display.vue';
import Button from './Button.vue'; // Optional

export default {
  components: { Display, Button },
  data() {
    return {
      currentNumber: '',
      result: '',
      operator: null,
    };
  },
  methods: {
    appendNumber(value) {
      // Handle invalid values (decimal at start, multiple decimals)
      if (isNaN(value) || (value === '.' && !this.currentNumber.includes('.'))) {
        return;
      }
      this.currentNumber += value;
    },
    setOperator(value) {
      // Ensure calculation on every operator change (optional)
      this.result = this.calculate();
      this.operator = value;
      this.currentNumber = '';
    },
    clear() {
      this.currentNumber = '';
      this.result = '';
      this.operator = null;
    },
    calculate() {
      // Robust error handling using try-catch
      try {
        if (this.operator && this.currentNumber) {
          const operation = new Function(
            'x',
            'y',
            `return ${this.operator}(x, y);`
          )(Number(this.result), Number(this.currentNumber));
          this.currentNumber = '';
          return operation;
        }
      } catch (error) {
        console.error('Error during calculation:', error);
        return 'Error';
      }
      return this.result;
    },
  },
};
</script>

<template>
<div class="calculator">
    <Display :currentNumber="currentNumber" :result="result" />
    <div class="button-container">
      <Button v-for="number in [1, 2, 3, '+']" :key="number" :value="number" @click="appendNumber" />
      <Button v-for="number in [4, 5, 6, '-']" :key="number" :value="number" @click="appendNumber" />
      <Button v-for="number in [7, 8, 9, '*']" :key="number" :value="number" @click="appendNumber" />
      <Button v-for="number in [0, '.', '=']" :key="number" :value="number" @click="appendNumber" />
      <Button :value="'/'" @click="setOperator" />
      <Button :value="$('C')" @click="clear" />
    </div>
  </div>
</template>

<style scoped>

</style>
