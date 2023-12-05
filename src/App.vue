<script setup>
import { reactive } from 'vue';

const estado = reactive ({
  operacao: 'soma',
  num1: '',
  num2: '',
});


function calculo (){
  const n1 = parseFloat(estado.num1);
  const n2 = parseFloat(estado.num2);

if(isNaN(n1) || isNaN(n2)){
  return 0
}

  switch (estado.operacao) {
    case 'subtracao':
      return n1 - n2;
    case 'divisao':
      return n1 / n2;
    case 'multiplicacao':
      return n1 * n2;
    default:
      return n1 + n2;
  };
};

calculo();

</script>

<template>
  <div class="container">
    <div class="mt-5">
      <h1>Calculadora</h1>
    </div>
    <div>
      <div class="calculadora">
        <input class="col-4 form-control" type="number" v-model="estado.num1" placeholder="Digite o primeiro número">        
        <select class="operacoes col-md-2 mt-3 mb-3 form-control" @change="evento => estado.operacao = evento.target.value">
          <option value="soma">+</option>
          <option value="subtracao">-</option>
          <option value="divisao">/</option>
          <option value="multiplicacao">*</option>
        </select>
        <input class="col-md-4 form-control" type="number" v-model="estado.num2" placeholder="Digite o segundo número">        
      </div>
      <div class="resultado">
        <h2>
          Resultado: {{ calculo(result) }}
        </h2>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .resultado{
    margin-top: 10px;
    padding: 10px 5px;
    background-color: #ebb31a;
    border-radius: .5cqw;
  }
</style>
