<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="site logo">
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="sortBy('title')">order by title</button>
        <button @click="sortBy('salary')">order by salary</button>
        <button @click="sortBy('location')">order by location</button>
      </div>
    </header>
    <JobList :jobs="jobs" :orderTerm="orderTerm"/>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import JobList from './components/JobsList.vue'
import Job from './types/Job'
import OrderFilter from './types/OrderFilter'

export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'farm worker', location: 'lon lon ranch', salary: 30000, id: '1' },
      { title: 'quarryman', location: 'death mountain', salary: 40000, id: '2' },
      { title: 'flute player', location: 'the lost woods', salary: 35000, id: '3' },
      { title: 'fisherman', location: 'lake hylia', salary: 21000, id: '4' },
      { title: 'prison guard', location: 'gerudo valley', salary: 32000, id: '5' }
    ])

    const orderTerm = ref<OrderFilter>('title')

    const sortBy = (filter: OrderFilter) => {
      orderTerm.value = filter
    }

    return { jobs, sortBy, orderTerm }
  }
});
</script>

<style>
  header {
    text-align: center;
  }
  header .order {
    margin-top: 20px;
  }
  button {
    color: #1195c9;
    margin: 0 10px;
    border: 3px solid #1195c9;
    background: #d5f0ff;
    padding: 8px 16px;
    border-radius: 4px;
    font-weight: bold;
    cursor: pointer;
  }
  header .title {
    display: flex;
    justify-content: center;
  }
  header img {
    width: 60px;
    margin-right: 20px;
  }
  header h1 {
    font-size: 3em;
  }
</style>
