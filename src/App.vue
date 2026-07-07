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
      return b !== 0
        ? (a / b).toFixed(2)
        : 'Não é possível dividir por zero.'

    default:
      return 0
  }
})
</script>

<template>
  <main class="container">
    <section class="card">

      <div class="title">
        <i class="fa-solid fa-calculator"></i>
        <h1>Calculadora Aritmética</h1>
      </div>

      <p class="subtitle">
        Escolha uma operação e informe os valores. O resultado será atualizado automaticamente.
      </p>

      <div class="campo">
        <label for="numero1">Primeiro número</label>

        <input id="numero1" v-model.number="num1" type="number" placeholder="Digite o primeiro número">
      </div>

      <div class="campo">
        <label for="operacao">Operação</label>

        <select id="operacao" v-model="operacao">
          <option value="+">Soma (+)</option>
          <option value="-">Subtração (-)</option>
          <option value="*">Multiplicação (*)</option>
          <option value="/">Divisão (÷)</option>
        </select>
      </div>

      <div class="campo">
        <label for="numero2">Segundo número</label>

        <input id="numero2" v-model.number="num2" type="number" placeholder="Digite o segundo número">
      </div>

      <div class="resultado">
        <small>
          <i class="fa-solid fa-equals"></i>
          Resultado
        </small>

        <h2>{{ resultado }}</h2>
      </div>

    </section>
  </main>
</template>

<style scoped>
@import "./style.css";
</style>