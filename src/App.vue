<script setup>
import { ref, computed } from 'vue'

const num1 = ref(0)
const num2 = ref(0)
const operacao = ref('+')

const resultado = computed(() => {
  const a = Number(num1.value)
  const b = Number(num2.value)

  switch (operacao.value) {
    case '+':
      return a + b
    case '-':
      return a - b
    case '*':
      return a * b
    case '/':
      return b !== 0 ? a / b : 'Erro: divisão por zero'
    default:
      return 0
  }
})
</script>

<template>
  <div class="container">
    <h1 class="title">Calculadora Aritmética</h1>

    <div class="card">
      <input
        v-model="num1"
        type="number"
        placeholder="Número 1"
      />

      <select v-model="operacao">
        <option value="+">Soma (+)</option>
        <option value="-">Subtração (-)</option>
        <option value="*">Multiplicação (*)</option>
        <option value="/">Divisão (/)</option>
      </select>

      <input
        v-model="num2"
        type="number"
        placeholder="Número 2"
      />

      <h2 class="result">
        Resultado: {{ resultado }}
      </h2>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 420px;
  margin: 60px auto;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  text-align: center;
}

.title {
  line-height: 1.4;
  font-size: 28px;
  margin-bottom: 10px;
}

.card {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

input,
select {
  padding: 10px;
  font-size: 16px;
  border-radius: 6px;
  border: 1px solid #ccc;
}

.result {
  margin-top: 10px;
  font-size: 20px;
  font-weight: bold;
}
</style>