<script setup>
import { reactive } from 'vue';



const contar = reactive({
  primeiroNumero:0,
  segundoNumero:0,
  operacao:'adicao',
  resultado:0
});

function calcular() {
  if(contar.operacao==='adicao') {
    contar.resultado= contar.primeiroNumero + contar.segundoNumero
  } else if (contar.operacao === 'subtracao') {
    contar.resultado = contar.primeiroNumero - contar.segundoNumero
  } else if (contar.operacao === 'multiplicacao') {
    contar.resultado = contar.primeiroNumero * contar.segundoNumero
  }else if (contar.operacao === 'divisao') {
    contar.resultado= contar.primeiroNumero / contar.segundoNumero
  }
}

function escolha(op, e){
  if(op === "primeiro"){
    if(e.target.value === ''){
      contar.primeiroNumero = 0
    }else{
      contar.primeiroNumero = parseInt(e.target.value)
    }
    calcular()
  }else if(op === "segundo"){
    if(e.target.value === ''){
      contar.segundoNumero = 0
    }else{
      contar.segundoNumero = parseInt(e.target.value)
    }
    calcular()
  }else if(op === "operacao"){
    contar.operacao = e.target.value
    calcular()
  }
}
</script>

<template>
<div class="container">
    <div class="text-center mt-5">
      <h1>Calculadora Aritmética
      </h1>
    </div>
    <div class="d-flex flex-column mt-4 align-items-center gap-3">
      <input type="number" class="w-25 form-control" @input="(e) => escolha('primeiro', e)" placeholder="Digite um número">
      <input type="number" class="w-25 form-control" @input="(e) => escolha('segundo', e)" placeholder="Digite um número">
      <select class="w-25 form-control"  @change="(e) => escolha('operacao', e)">
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="multiplicacao">Multiplicação</option>
        <option value="divisao">Divisão</option>
      </select>
    </div>
    <div class="d-flex justify-content-center mt-4">
      <h2>Resultado: {{ contar.resultado }}</h2>
    </div>
  </div>
</template>

<style scoped>

</style>
