<template>
  <div id="app">
    <h1>Calculadora Aritmética</h1>

    <!-- Campos para inserir os números -->
    <input v-model.number="numero1" type="number" placeholder="Insira o primeiro número" />
    <input v-model.number="numero2" type="number" placeholder="Insira o segundo número" />

    <!-- Seleção da operação -->
    <select v-model="operacao">
      <option value="adicao">+</option>
      <option value="subtracao">-</option>
      <option value="multiplicacao">*</option>
      <option value="divisao">/</option>
    </select>

    <!-- Resultado -->
    <h2>Resultado: {{ resultado }}</h2>
  </div>
</template>

<script setup>
// Variáveis reativas
import { ref, computed } from 'vue'

const numero1 = ref(0)
const numero2 = ref(0)
const operacao = ref('adicao')

// Computed para calcular o resultado com base na operação
const resultado = computed(() => {
  switch (operacao.value) {
    case 'adicao':
      return numero1.value + numero2.value
    case 'subtracao':
      return numero1.value - numero2.value
    case 'multiplicacao':
      return numero1.value * numero2.value
    case 'divisao':
      return numero2.value !== 0 ? numero1.value / numero2.value : 'Erro: Divisão por zero'
    default:
      return 0
  }
})
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 40px;
}

input {
  margin: 10px;
  padding: 5px;
  font-size: 16px;
}

select {
  margin: 10px;
  padding: 5px;
  font-size: 16px;
}

h2 {
  margin-top: 20px;
  color: #42b983;
}
</style>
