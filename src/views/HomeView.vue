<script setup>
// import Dashboard from '../components/Dashboard.vue'
import { ref, onMounted } from 'vue'
import { __currency } from '../composables/helpers'

const transactions = ref([])

const expenses = ref([])
const gains = ref([])

onMounted(() => {
  const storedTransactions = localStorage.getItem('transactions')

  if (storedTransactions) {
    transactions.value = JSON.parse(storedTransactions)
  }

  expenses.value = transactions.value.filter((transaction) => transaction.type === 'expense')
  gains.value = transactions.value.filter((transaction) => transaction.type === 'gain')
})
</script>

<template>
  <main>
    <h1>Dashboard 📊</h1>

    <div>
      <h3>Contas a pagar 🔴</h3>

      <p v-for="expense in expenses" key="index">
        {{ __currency(expense.value) }}
      </p>
    </div>

    <br />

    <div>
      <h3>Entradas 🟢</h3>

      <p v-for="gain in gains" key="index">
        {{ __currency(gain.value) }}
      </p>
    </div>

    <!-- <Dashboard /> -->
  </main>
</template>
