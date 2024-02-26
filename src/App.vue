<template>
  <div class="container bg-theme d-flex justify-content-between">
    <div class="sidebar d-flex justify-content-between">
      <IncomeExpense :income="Number(income)" :expense="Number(expense)" />
      <TransactionList
        :transactions="transactions"
        @transaction-deleted="handleTransactionDeleted"
      />
    </div>
    <div class="main d-flex justify-content-between">
      <Balance :total="Number(total)" />
      <AddTransaction @transaction-submitted="handleTransactionSubmitted" />
    </div>
  </div>
</template>

<script setup>
import IncomeExpense from "./components/IncomeExpense.vue";
import TransactionList from "./components/TransactionList.vue";
import Balance from "./components/Balance.vue";
import AddTransaction from "./components/AddTransaction.vue";

import { computed, onMounted, ref } from "vue";

// 帳務紀錄
const transactions = ref([]);

// 新增帳務
const handleTransactionSubmitted = (newData) => {
  transactions.value.push({
    id: generateUniqueId(),
    text: newData.text,
    amount: newData.amount,
  });

  saveToLocalStorage();
};

// 總額顯示
// 第一個 return 作為 computed 屬性回傳；第二個 return 作為 .reduce() 回傳值
const total = computed(() => {
  return transactions.value.reduce((acc, transaction) => {
    return acc + transaction.amount;
  }, 0);
});

// 收入顯示
const income = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount > 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0);
});

// 支出顯示
const expense = computed(() => {
  return transactions.value
    .filter((transaction) => transaction.amount < 0)
    .reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0);
});

// 刪除項目
const handleTransactionDeleted = (id) => {
  transactions.value = transactions.value.filter(
    (transaction) => transaction.id !== id
  );

  saveToLocalStorage();
};

// ID產生
const generateUniqueId = () => {
  return Math.floor(Math.random() * 1000000);
};

// LocalStorage
const saveToLocalStorage = () => {
  localStorage.setItem("vet-transactions", JSON.stringify(transactions.value));
};

// onMounted

onMounted(() => {
  const savedTransactions = JSON.parse(
    localStorage.getItem("vet-transactions")
  );

  if (savedTransactions) {
    transactions.value = savedTransactions;
  }
});
</script>
