<template>
  <div class="add-container">
    <h2 class="mb-3 h2">Add new transaction</h2>
    <form id="form" @submit.prevent="onSubmit">
      <div class="form-container d-flex">
        <div class="form-control">
          <label for="text"
            >Text
            <input
              v-model="text"
              type="text"
              id="text"
              placeholder="Enter text..."
            />
          </label>
        </div>
        <div class="form-control">
          <label for="amount"
            >Amount
            <div class="d-flex">
              <button type="button" class="posNeg-btn" @click="posNegSwitch">
                {{ posNeg }}
              </button>
              <input v-model="amount" type="text" id="amount" />
            </div>
          </label>
        </div>
        <button class="align-self-end">ADD</button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const emit = defineEmits(["transactionSubmitted"]);

const text = ref("");
const amount = ref("");
const posNeg = ref("-");

const onSubmit = () => {
  if (!text.value || !amount.value) {
    return alert("All field must be filled!");
  }
  if (isNaN(Number(amount.value))) {
    return alert("must be numbers");
  }
  const newData = {
    text: text.value,
    amount: parseFloat(amount.value),
  };

  emit("transactionSubmitted", newData);

  text.value = "";
  amount.value = "";
};

const posNegSwitch = () => {
  if (posNeg.value == "+") {
    amount.value = "";
    posNeg.value = "-";
  } else {
    amount.value = "-";
    posNeg.value = "+";
  }
};
</script>
