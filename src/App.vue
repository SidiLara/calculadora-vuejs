<script setup>
import { reactive } from 'vue';

const estado = reactive({
  valor1: 0,
  valor2: 0,
  aritmetica: ''
});

const soma = () => estado.valor1 + estado.valor2;
const subtrai = () => estado.valor1 - estado.valor2;
const multiplica = () => estado.valor1 * estado.valor2;
const divide = () => estado.valor1 / estado.valor2;


const getCalculo = () => {
  switch (estado.aritmetica) {
    case 'soma':
      return soma();
    case 'diminui':
      return subtrai();
    case 'multiplica':
      return multiplica();
    case 'divide':
      return divide();
    default:
      return 0;
  }
};
</script>

<template>
  <form class="d-flex justify-content-center mt-5">
    <div class="card" style="width: 18rem;">
      <div class="container">
        <h1 class="text-center">Calculadora</h1>
        <div class="border bg-dark text-light rounded-2">
          <h2 class="text-center" style="font-size: 48px;">{{ getCalculo() }}</h2>
        </div>
        <div class="row align-items-center">
          <div class="col">
            <div class="mt-3">
              <label class="fw-bold" for="valor1">Valor 1</label>
              <input type="number" v-model.number="estado.valor1" class="form-control" placeholder="Primeiro valor">
            </div>
            <div class="mt-3 mb-2">
              <label class="fw-bold" for="valor2">Valor 2</label>
              <input name="valor2" type="number" v-model.number="estado.valor2" class="form-control"
                placeholder="Segundo valor">
            </div>
          </div>
          <div class="col mt-3">
            <select @change="evento => estado.aritmetica = evento.target.value" class="form-select border border-black"
              aria-label="calculo">
              <option selected>Calcular</option>
              <option value="soma">+</option>
              <option value="diminui">-</option>
              <option value="multiplica">*</option>
              <option value="divide">/</option>
            </select>
          </div>
        </div>
      </div>
    </div>
  </form>
</template>
