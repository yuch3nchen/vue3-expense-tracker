<template>
  <div class="container bg-theme d-flex justify-content-between">
    <div class="sidebar d-flex justify-content-between">
      <div class="inc-exp-container d-flex justify-content-between mb-1">
        <div class="income">
          <h3 class="mb-4 h3">Income</h3>
          <p class="plus h5">$100</p>
        </div>
        <div class="expense">
          <h3 class="mb-4 h3">Expense</h3>
          <p class="minus h5">-$50</p>
        </div>
      </div>
      <div class="history-container d-flex justify-content-between">
        <h2 class="h2">History</h2>
        <ul class="list">
          <li class="d-flex justify-content-between">
            Shopping
            <span class="minus">-$50</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
          <li class="d-flex justify-content-between">
            Salary
            <span class="plus">$100</span>
          </li>
        </ul>
      </div>
    </div>
    <div class="main d-flex justify-content-between">
      <div class="balance-container">
        <h2 class="h2">Balance</h2>
        <h1 class="balance text-end plus h1">$1000</h1>
      </div>
      <div class="add-container">
        <h2 class="mb-3 h2">Add new transaction</h2>
        <form @onSubmit.prevent>
          <div class="form-container d-flex">
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
  </div>
</template>

<script setup></script>
