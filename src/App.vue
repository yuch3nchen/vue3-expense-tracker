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

<style scoped>
.container {
  width: 90vw;
  height: 100%;
  max-width: 800px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 1rem 0.75rem;
  border-radius: 6px;
  box-shadow: rgba(27, 31, 35, 0.04) 0px 1px 0px,
    rgba(255, 255, 255, 0.25) 0px 1px 0px inset;
  gap: 1.25rem;
  flex-direction: column;

  @media screen and (min-width: 767px) {
    height: 50vh;
    width: 70vw;
    padding-top: 1.5rem;
    padding-bottom: 1.5rem;
    flex-direction: row;
  }
}

.main {
  flex: 1 0 40%;
  flex-direction: column;
  gap: 1.5rem;

  @media screen and (min-width: 767px) {
    height: 100%;
  }

  @media screen and (min-width: 992px) {
    flex: 1 0 60%;
  }
}

.sidebar {
  flex: 1 0 50%;
  flex-direction: column;

  @media screen and (min-width: 767px) {
    height: 100%;
  }

  @media screen and (min-width: 992px) {
    flex: 1 0 30%;
  }
}
</style>
