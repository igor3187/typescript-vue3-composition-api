<script setup lang="ts">
import { ref } from 'vue'
import type Job from '@/types/Job'
import JobsList from '@/components/JobsList.vue'
import type OrderTerm from '@/types/OrderTerm'

const jobs = ref<Job[]>([
  { id: '1', title: 'farm worker', location: 'village', salary: 3000 },
  { id: '2', title: 'office worker', location: 'city', salary: 4000 },
  { id: '3', title: 'flute player', location: 'the lost world', salary: 5000 },
  { id: '4', title: 'fisherman', location: 'lake', salary: 6000 },
  { id: '5', title: 'policeman', location: 'london', salary: 7000 }
])

const order = ref<OrderTerm>('title')

const orderBy = (term: OrderTerm) => {
  order.value = term
}
</script>

<template>
  <div class="app">
    <header>
      <div class="title">
          <img src="@/assets/reshot-icon-gazelle-6VPBHZEDFA.svg" alt="Logo">
          <h1>Top Jobs</h1>
      </div>
      <div class="order">
        <button @click="orderBy('title')">Order by title</button>
        <button @click="orderBy('salary')">Order by salary</button>
        <button @click="orderBy('location')">Order by location</button>
      </div>
    </header>
    <JobsList :jobs="jobs" :order="order" />
  </div>
</template>

<style scoped>
button {
  border-radius: 4px;
  border: 1px solid blueviolet;
  padding: 10px;
  margin: 20px 20px 0 0;
  min-width: 120px;
  background: aliceblue;
  font-weight: bolder;
}

.title {
  display: flex;
}

img {
  width: 50px;
}
</style>
