<template>
  <div class='p-5 max-w-4xl bg-black m-16'>

    <!--  Résultat de la calculatrice -->
    <div class='w-full rounded-full m-1 p-6 text-right leading-normal font-bold text-white bg-gray-800'>
      {{ props.calculatorValue || 0 }}
    </div>
  </div>
</template>

<script setup>

const props = defineProps({
  calculatorValue: {
    type: String,
    required: true
  }
})


</script>
