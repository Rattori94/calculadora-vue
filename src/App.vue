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
        <h1>Calculadora Vue</h1>
      </div>

      <p class="subtitle">
        Escolha uma operação e informe os números. O resultado será atualizado automaticamente.
      </p>

      <div class="campo">
        <label for="num1">Primeiro número</label>

        <input
          id="num1"
          v-model.number="num1"
          type="number"
          placeholder="Digite o primeiro número"
        >
      </div>

      <div class="operacoes">

        <button
          type="button"
          class="op-btn"
          :class="{ ativo: operacao === '+' }"
          @click="operacao = '+'"
        >
          <i class="fa-solid fa-plus"></i>
        </button>

        <button
          type="button"
          class="op-btn"
          :class="{ ativo: operacao === '-' }"
          @click="operacao = '-'"
        >
          <i class="fa-solid fa-minus"></i>
        </button>

        <button
          type="button"
          class="op-btn"
          :class="{ ativo: operacao === '*' }"
          @click="operacao = '*'"
        >
          <i class="fa-solid fa-xmark"></i>
        </button>

        <button
          type="button"
          class="op-btn"
          :class="{ ativo: operacao === '/' }"
          @click="operacao = '/'"
        >
          <i class="fa-solid fa-divide"></i>
        </button>

      </div>

      <div class="campo">
        <label for="num2">Segundo número</label>

        <input
          id="num2"
          v-model.number="num2"
          type="number"
          placeholder="Digite o segundo número"
        >
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