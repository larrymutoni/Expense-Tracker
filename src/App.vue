
<script setup>
  import { ref, computed } from 'vue';
  import Header from './components/Header.vue';
  import Balance from './components/Balance.vue';
  import IncomeExpenses from './components/IncomeExpenses.vue';
  import TransactionList from './components/TransactionList.vue';
  import AddTransaction from './components/AddTransaction.vue';


 

  const transactions= ref([
        {
            id:1, text: 'Flower', amount: -19.99
        },
        {
            id:2, text: 'Salary', amount: 299.97
        },
        {
            id:3, text: 'Book', amount: -10
        },
        {
            id:4, text: 'Camera', amount: 150
        },
  ])

  const total = computed(() => {
    return transactions.value.reduce((acc, transaction) => {
      return acc + transaction.amount;
    }, 0)
  });
</script>

<template>
  <Header />
  <div class="container">
     <Balance :total="total" />
     <IncomeExpenses />
     <TransactionList :transactions="transactions" />
     <AddTransaction />  
  </div>
</template>