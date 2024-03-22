<script setup>
import { reactive } from 'vue';

  const dadosReativos = reactive({
    operacao: 'soma',
    operador: '+',
    operando1: 0,
    operando2: 0,
    resultado: 0
  })

  const trocarOperacao = () => {
    const { operacao, operando1, operando2 } = dadosReativos;
    
    switch (operacao) {
      case 'soma':
        dadosReativos.operador = '+';
        dadosReativos.resultado = operando1 + operando2;
        break
      case 'subtracao':
        dadosReativos.operador = '-';
        dadosReativos.resultado = operando1 - operando2;
        break
      case 'multiplicacao':
        dadosReativos.operador = '*';
        dadosReativos.resultado = operando1 * operando2;
        break
      case 'divisao':
        dadosReativos.operador = '÷';
        if (operando2 !== 0) {
        dadosReativos.resultado = operando1 / operando2;
      } else {
        dadosReativos.resultado = 0;
      }
        break
      default:
        dadosReativos.operador = '';
        dadosReativos.resultado = 0;
    }
  }
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-dark rounded-3">
        <h1 class="text-light text-center">Calculadora Aritmética</h1>
    </header>
    <form>
        <div class="row">
          <div class="col-md-3">
            <select v-model="dadosReativos.operacao" @change="trocarOperacao" class="form-control"> <!-- Usar o @change -->
              <option value="soma">Soma</option>
              <option value="subtracao">Subtração</option>
              <option value="multiplicacao">Multiplicação</option>
              <option value="divisao">Divisão</option>
            </select>
          </div>
          <div class="col-md-3">
            <input type="number" placeholder="0" class="form-control" v-model="dadosReativos.operando1" @keyup="trocarOperacao">
          </div>
          <div class="text-center col-md-1">
            <span class="h3">
              {{ dadosReativos.operador }}
            </span>
          </div>
          <div class="col-md-3">
            <input type="number" placeholder="0" class="form-control" v-model="dadosReativos.operando2" @keyup="trocarOperacao">
          </div>
        </div>
        <div class="row mt-3">
          <div class="col-md-6">
            <h4>Primeiro operando: {{ dadosReativos.operando1 }}</h4>
            <br>
            <h4>Segundo operando: {{ dadosReativos.operando2 }}</h4>
            <br>
            <h4>Resultado: {{ dadosReativos.resultado }}</h4>    
          </div>
        </div>
    </form>
  </div>
</template>

<style scoped>

</style>