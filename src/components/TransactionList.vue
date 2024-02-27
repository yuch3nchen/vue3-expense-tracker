<template>
  <div class="history-container d-flex">
    <h2 class="h2">History</h2>
    <ul class="scrollable-list">
      <li
        v-for="transaction in transactions"
        :key="transaction.id"
        class="list-item d-flex justify-content-between"
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

<style scoped>
.history-container {
  height: 70%;
  flex-direction: column;
  gap: 1rem;
}

.scrollable-list {
  overflow-y: scroll;
}

.list-item {
  padding: 0.25rem 0.5rem;
  position: relative;
}

.list-item:not(:last-child) {
  margin-bottom: 0.5rem;
}

.delete-btn {
  padding: 0 0.5rem;
  position: absolute;
  top: 50%;
  right: 0;
  transform: translate(-100%, -50%);
  border: none;
  border-radius: 0%;
  color: var(--theme-danger-color);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.delete-btn:hover {
  background-color: transparent;
}

.list-item:hover .delete-btn {
  opacity: 1;
  color: var(--theme-danger-color);
}
</style>
