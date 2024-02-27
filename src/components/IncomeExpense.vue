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

<style scoped>
.inc-exp-container {
  border: 1px dashed var(--theme-font-color);
  border-radius: 4px;
  padding: 0.5rem 0.75rem;
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
  gap: 0.5rem;
  flex-direction: column;
  align-items: center;

  @media screen and (min-width: 349px) {
    flex-direction: row;
  }
}

.inc-exp-container > div {
  flex: 1;
}
</style>
