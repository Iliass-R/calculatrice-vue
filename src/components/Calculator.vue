<template>
  <div class='p-5 max-w-4xl bg-black m-20 h-2/4'>

    <!--  Résultat de la calculatrice -->
    <div class='w-full rounded-full m-1 mx-1 p-4 text-right font-bold text-white bg-gray-800'>
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
