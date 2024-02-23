<template>
  <div class="container bg-theme d-flex justify-content-between">
    <div class="sidebar">
      <div class="inc-exp-container d-flex justify-content-between mb-1">
        <div class="income">
          <h4 class="mb-4">Income</h4>
          <p class="plus h5">$100</p>
        </div>
        <div class="expense">
          <h4 class="mb-4">Expense</h4>
          <p class="minus h5">-$50</p>
        </div>
      </div>
      <h2 class="mb-3">History</h2>
      <ul class="list">
        <li class="d-flex justify-content-between">
          Shopping
          <span class="minus">-$50</span>
        </li>
        <li class="d-flex justify-content-between">
          Salary
          <span class="plus">$100</span>
        </li>
      </ul>
    </div>
    <div class="main">
      <div class="balance-container mb-1">
        <h3>Balance</h3>
        <h1 class="balance text-end plus">$1000</h1>
      </div>
      <h2 class="mb-3">Add new transaction</h2>
      <form @onSubmit.prevent>
        <div class="add-container d-flex">
          <div class="form-control">
            <label for="text"
              >Text <input type="text" id="text" placeholder="Enter text..."
            /></label>
          </div>
          <div class="form-control">
            <label for="amount"
              >Amount
              <input type="text" id="amount" />
            </label>
          </div>
          <button class="align-self-end">ADD</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script setup></script>
