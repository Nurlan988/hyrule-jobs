<template>
  <div class="app">
    <header>
      <div class="title">
        <h1>Remote work</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">order by title</button>
        <button @click="handleClick('salary')">order by salary</button>
        <button @click="handleClick('location')">order by location</button>
      </div>
    </header>
    <job-list :jobs="jobs" :order="order"></job-list>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobList from './components/JobList.vue'
import Job from './types/Job'
import OrderTerm from './types/OrderTerm'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'Frontend Vue.js', location: 'London', salary: 3000, id: '1' },
      { title: 'Frontend React', location: 'New York', salary: 4000, id: '2' },
      { title: 'Backend Java', location: 'Moscow', salary: 3500, id: '3' },
      { title: 'Backend PHP', location: 'Baku', salary: 2100, id: '4' },
      { title: 'UI/UX Designer', location: 'Berlin', salary: 3200, id: '5' }
    ])
    const order = ref<OrderTerm>('title')

    const handleClick = (term: OrderTerm) => {
      order.value = term
    }

    return { jobs, handleClick, order };
  }
})
</script>

<style>
header {
  text-align: center;
}

header .order {
  margin-top: 20px;
}

button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
</style>
