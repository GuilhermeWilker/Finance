<script setup>
import { ref } from 'vue'
import { Bar } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
} from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

const chartData = ref({
  labels: ['Entradas', 'Despesas'],
  datasets: [{ data: [40, 20, 12] }]
})

const chartOptions = ref({
  responsive: true
})
</script>

<template>
  <div class="dashboard__view">
    <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
  </div>
</template>

<style scoped>
.dashboard__view {
  border: 1px solid red;
  margin: 1em auto;

  padding: 0.5em;
  height: 32em;
  width: 95%;

  overflow: hidden;
}
</style>
