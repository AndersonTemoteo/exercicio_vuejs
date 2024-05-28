<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    numeroUm: 0,
    nummeroDois: 0,
    resultado: 0,
    filtro: 'soma',
  })

  const fazCalculo = () => {
    const {filtro} = estado;

    switch (filtro) {
      case 'subtracao':
        return parseFloat(estado.numeroUm) - parseFloat(estado.nummeroDois);
      case 'multiplicacao':
        return parseFloat(estado.numeroUm) * parseFloat(estado.nummeroDois);
      case 'divisao':
        return parseFloat(estado.numeroUm) / parseFloat(estado.nummeroDois);
      default:
        return parseFloat(estado.numeroUm) + parseFloat(estado.nummeroDois);
    }
  }

</script>

<template>
  <div class="container p-5 mb-4 mt-4 bg-light rounded-3">
    <h1>Calculadora Aritmética</h1>
    <form>
      <div class="row pt-3">
        <input type="number" required placeholder="Digite o primeiro número" class="form-control" @change="evento => estado.numeroUm = evento.target.value">
      </div>
      <div class="row pt-3">
        <input type="number" required placeholder="Digite o segundo número" class="form-control" @change="evento => estado.nummeroDois = evento.target.value">
      </div>
      <div class="row pt-3">
        <select @change="evento => estado.filtro = evento.target.value" class="form-control">
          <option value="soma">Soma ( + )</option>
          <option value="subtracao">Subtração ( - )</option>
          <option value="multiplicacao">Multiplicação ( * )</option>
          <option value="divisao">Divisão ( / )</option>
        </select>
        <span class="pt-4 fw-semibold fs-4"> Resultado: {{ fazCalculo() }}</span>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
