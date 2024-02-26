<template>
  <div class="balance-container">
    <h2 class="h2">Balance</h2>
    <h1 :class="total < 0 ? 'minus' : 'plus'" class="balance text-end h1">
      $&nbsp;{{ isNaN(total) ? 0 : total }}
    </h1>
  </div>
</template>

<script setup>
const props = defineProps({
  total: {
    type: Number,
    required: true,
  },
});
</script>
