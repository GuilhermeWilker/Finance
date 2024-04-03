<script setup>
import Dashboard from '../components/Dashboard.vue'
import { ref, onMounted } from 'vue'

const transactions = ref([])

onMounted(() => {
  const storedTransactions = localStorage.getItem('transactions')

  if (storedTransactions) {
    transactions.value = JSON.parse(storedTransactions)
  }
})
</script>

<template>
  <main>
    <h1>Dashboard 📊</h1>

    <div v-for="transaction in transactions" key="index">
      <p>{{ transaction.type }} | {{ transaction.value }}</p>
    </div>

    <!-- <Dashboard /> -->
  </main>
</template>
