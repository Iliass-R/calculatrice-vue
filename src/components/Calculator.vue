<template>
  <section class="h-auto bg-white tails-selected-element text-center">
    <p class="mt-10 text-4xl font-extrabold text-gray-900 sm:text-5xl sm:tracking-tight lg:text-6xl">Calculatrice</p>
    <p class="max-w-3xl mt-5 mx-auto text-xl text-gray-500">Faite avec Vue3 Vite et Tailwind CSS</p>

    <div class='p-5 mt-8 max-w-md bg-black m-auto w-8/12 h-2/4 rounded-lg'>

      <!--  Résultat de la calculatrice -->
      <div class='mx-auto w-full rounded-full m-1 p-4 text-right font-bold text-white bg-gray-800'>
        {{ calculatorValue || 0 }}
      </div>

      <!-- Boutons de la calculatrice -->
      <div class='grid grid-cols-4 gap-2 p-2 h-auto'>
        <div class='' v-for="n in calculatorElements" :key="n">
          <div
            class='text-white text-center leading-normal mx-1 py-2.5 bg-gray-800 rounded-2xl cursor-pointer hover:bg-gray-600'
            :class="{'bg-yellow-600': ['-','+','%','/','*', 'C','='].includes(n)}" @click="(action(n))">
            {{ n }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';
const calculatorElements = ['C', '*', '/', '-', '7', '8', '9', '+', '4', '5', '6', '%', '1', '2', '3', '=', '0', '.']

var calculatorValue = ref('');

// Fonction qui gère les actions de la calculatrice
const action = (n) => {
  if (n === 'C') {
    calculatorValue.value = '';
  } else if (n === '=') {
    calculatorValue.value = eval(calculatorValue.value);
  } else if (n === '%') {
    calculatorValue.value = calculatorValue.value / 100;
  } else {
    calculatorValue.value += n;
  }
  console.log(calculatorValue.value);
}

</script>
