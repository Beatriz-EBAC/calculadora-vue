<script setup>
import { ref, computed } from 'vue'

const numero1 = ref('')
const numero2 = ref('')
const operacao = ref('soma')

const resultado = computed(() => {
  if (numero1.value === '' || numero2.value === '') return ''

  const a = Number(numero1.value)
  const b = Number(numero2.value)

  switch (operacao.value) {
    case 'soma':
      return a + b
    case 'subtracao':
      return a - b
    case 'multiplicacao':
      return a * b
    case 'divisao':
      return b === 0 ? 'Não é possível dividir por zero' : a / b
    default:
      return ''
  }
})
</script>

<template>
  <main class="calculadora">
    <h1>Calculadora Vue</h1>
    <p>Operações aritméticas em tempo real</p>

    <input v-model="numero1" type="number" placeholder="Primeiro número">

    <select v-model="operacao">
      <option value="soma">Adição (+)</option>
      <option value="subtracao">Subtração (-)</option>
      <option value="multiplicacao">Multiplicação (×)</option>
      <option value="divisao">Divisão (÷)</option>
    </select>

    <input v-model="numero2" type="number" placeholder="Segundo número">

    <section class="resultado">
      <span>Resultado</span>
      <strong>{{ resultado === '' ? '—' : resultado }}</strong>
    </section>
  </main>
</template>