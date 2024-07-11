<template>
<div id="app">
      <h1>Calculadora Rápida e Prática</h1>
      <div class="numbers">
        <input class="input-number" type="number" v-model.number="num1" @input="calculate" />
        <select class="selecao" v-model="operation" @change="calculate">
          <option value="add">+</option>
          <option value="subtract">-</option>
          <option value="multiply">*</option>
          <option value="divide">/</option>
        </select>
        <input class="input-number" type="number" v-model.number="num2" @input="calculate" />
      </div>
      <h2> O resultado: {{ result }}</h2>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const num1 = ref(0);
const num2 = ref(0);
const operation = ref('add');
const result = ref(null);

const calculate = () => {
  switch (operation.value) {
    case 'add':
      result.value = num1.value + num2.value;
      break;
    case 'subtract':
      result.value = num1.value - num2.value;
      break;
    case 'multiply':
      result.value = num1.value * num2.value;
      break;
    case 'divide':
      result.value = num2.value !== 0 ? num1.value / num2.value : 'Erro. Divisão por zero.';
      break;
  }
};
</script>

<style>
html, body {
  height: 100%;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

#app {
  display: flex;
  margin: 0 auto;
  flex-direction: column;
  align-items: center;
  text-align: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 20px;
  background-color: #ccc;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.numbers {
  display: flex;
  align-items: center;
  margin: 20px 0;
}

.input-number, .selecao {
  width: 100px; 
  height: 40px; 
  margin: 0 8px; 
  text-align: center; 
  border: 1px solid #ccc; 
  border-radius: 5px;
  font-size: 16px;
}
</style>