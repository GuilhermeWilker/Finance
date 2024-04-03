<template>
  <form action="" class="form">
    <legend>Adicione uma nova entrada</legend>

    <div class="form-group">
      <label for="tipo-transacao">Tipo de Transação</label>
      <select v-model="option">
        <option value="gain">Ganho</option>
        <option value="expense">Despesa</option>
      </select>
    </div>

    <div class="form-group">
      <label for="">Valor:</label>
      <input type="text" v-model="valor" placeholder="R$ 0,00" />
    </div>

    <button type="submit" @click.prevent="submitForm">Cadastrar Entrada</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const option = ref('gain')
const valor = ref('')
const transactions = ref([])

const submitForm = () => {
  const transaction = {
    type: option.value,
    value: valor.value
  }
  transactions.value.push(transaction)
  localStorage.setItem('transactions', JSON.stringify(transactions.value))

  option.value = 'gain'
  valor.value = ''
}
</script>

<style scoped>
.form {
  margin: 2em auto;
  border: 1px solid white;
  padding: 1em;
  border-radius: 0.3em;
  width: 70%;
}

.form-group {
  width: 100%;
  margin-block: 0.8em;
}

.form-group label {
  display: block;
  font-size: 0.9em;
}

.form-group input,
.form-group select {
  width: 100%;
  padding: 0.4em 0.8em;
}

.form button {
  width: 100%;
  padding: 0.7em;
  border: 1px solid #fff;
  background-color: rgb(52, 52, 224);
  color: white;
  cursor: pointer;
}

.form button:hover {
  background-color: rgb(36, 36, 175);
}
</style>
