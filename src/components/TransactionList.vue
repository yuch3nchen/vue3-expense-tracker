<template>
  <div class="history-container d-flex">
    <h2 class="h2">History</h2>
    <ul class="list">
      <li
        v-for="transaction in transactions"
        :key="transaction.id"
        class="d-flex justify-content-between"
      >
        {{ transaction.text }}
        <span :class="transaction.amount < 0 ? 'minus' : 'plus'"
          >$&nbsp;{{ transaction.amount }}</span
        >
        <button @click="deleteTransaction(transaction.id)" class="delete-btn">
          delete?
        </button>
      </li>
    </ul>
  </div>
</template>

<script setup>
const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["transactionDeleted"]);

const deleteTransaction = (id) => {
  emit("transactionDeleted", id);
};
</script>
