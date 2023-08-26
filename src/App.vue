<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numeroA:0,
  numeroB:0,
  operacao:'adicao',
})

const somar=()=>{
  const numA = parseFloat(estado.numeroA);
  const numB = parseFloat(estado.numeroB);
  return numA + numB;
}

const subtrair=()=>{
  const numA = parseFloat(estado.numeroA);
  const numB = parseFloat(estado.numeroB);
  return numA - numB;
}

const multiplicar=()=>{
  const numA = parseFloat(estado.numeroA);
  const numB = parseFloat(estado.numeroB);
  return numA * numB;
}

const dividir=()=>{
  const numA = parseFloat(estado.numeroA);
  const numB = parseFloat(estado.numeroB);
  return numA / numB;
}

const resultadoOperacao = () => {
    const {operacao} = estado;

    switch(operacao) {
        case 'subtracao':
            return subtrair();
        case 'multiplicacao':
            return multiplicar();
        case 'divisao':
            return dividir();    
        default:
            return somar();
    }
}

</script>

<template>
  <header><h1>Calculadora</h1></header>
  <section>
    <div class="row justify-content-center w-auto m-auto fs-4">
      <div class="col-md-2 w-auto p-0">
        <input @change="evento=>estado.numeroA=evento.target.value" type="number" placeholder="digite um número">
      </div>
      <div class="col-md-1 w-auto p-0">
        <select @change="evento=>estado.operacao = evento.target.value" class="fs-2em">
          <option value="adicao">+</option>
          <option value="subtracao">-</option>
          <option value="multiplicacao">*</option>
          <option value="divisao">/</option>
        </select>
      </div>
      <div class="col-md-2 w-auto p-0">
        <input @change="evento=>estado.numeroB=evento.target.value" type="number" placeholder="digite outro número">
      </div>
      <div class="col-md-1 w-auto p-0">
        <p> = {{resultadoOperacao()}}</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
* {
  padding: 0;
  margin: 0;
  text-align: center;
}
</style>
