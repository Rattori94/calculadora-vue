<script setup>
import { ref } from 'vue'

const num1 = ref(null)
const num2 = ref(null)

const operacao = ref('+')

const resultado = ref(null)

function calcular() {
  const a = Number(num1.value)
  const b = Number(num2.value)

  switch (operacao.value) {
    case '+':
      resultado.value = a + b
      break

    case '-':
      resultado.value = a - b
      break

    case '*':
      resultado.value = a * b
      break

    case '/':
      resultado.value =
        b !== 0
          ? (a / b).toFixed(2)
          : 'Não é possível dividir por zero.'
      break
  }
}
</script>

<template>
  <main class="container">

    <section class="card">

      <div class="title">

        <i class="fa-solid fa-calculator"></i>

        <h1>Calculadora Vue</h1>

      </div>

      <p class="subtitle">
        Escolha uma operação, informe os números e clique em calcular.
      </p>

      <div class="campo">

        <label>
          Primeiro número
        </label>

        <input
          v-model.number="num1"
          type="number"
          placeholder="Digite um número"
        >

      </div>

      <div class="operacoes">

        <button
          class="op-btn"
          :class="{ ativo: operacao === '+' }"
          @click="operacao = '+'"
        >
          <i class="fa-solid fa-plus"></i>
        </button>

        <button
          class="op-btn"
          :class="{ ativo: operacao === '-' }"
          @click="operacao = '-'"
        >
          <i class="fa-solid fa-minus"></i>
        </button>

        <button
          class="op-btn"
          :class="{ ativo: operacao === '*' }"
          @click="operacao = '*'"
        >
          <i class="fa-solid fa-xmark"></i>
        </button>

        <button
          class="op-btn"
          :class="{ ativo: operacao === '/' }"
          @click="operacao = '/'"
        >
          <i class="fa-solid fa-divide"></i>
        </button>

      </div>

      <div class="campo">

        <label>
          Segundo número
        </label>

        <input
          v-model.number="num2"
          type="number"
          placeholder="Digite outro número"
        >

      </div>

      <button
        class="calcular"
        @click="calcular"
      >
        <i class="fa-solid fa-equals"></i>

        Calcular
      </button>

      <Transition name="fade">

        <div
          v-if="resultado !== null"
          class="resultado"
        >

          <small>Resultado</small>

          <h2>{{ resultado }}</h2>

        </div>

      </Transition>

    </section>

  </main>
</template>

<style scoped>
@import "./style.css";
</style>
```
