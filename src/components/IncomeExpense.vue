<template>
  <div class="inc-exp-container d-flex justify-content-between mb-1">
    <div class="income">
      <h3 class="mb-4 h3">Income</h3>
      <p class="plus h5">$&nbsp;{{ income }}</p>
    </div>
    <div class="expense">
      <h3 class="mb-4 h3">Expense</h3>
      <p class="minus h5">$&nbsp;{{ expense }}</p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  income: {
    type: Number,
    required: true,
  },
  expense: {
    type: Number,
    required: true,
  },
});
</script>
