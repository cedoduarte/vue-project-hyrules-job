<template>
  <div class="app">
    <header>
      <div>
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="handleClick('title')">Order by title</button>
        <button @click="handleClick('salary')">Order by salary</button>
        <button @click="handleClick('location')">Order by location</button>
      </div>
    </header>

    <JobListComponent :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive, toRefs } from 'vue';
import { Job } from "./types/Job";
import JobListComponent from './components/JobListComponent.vue';
import OrderTerm from "./types/OrderTerm";

export default defineComponent({
  name: 'App',
  components: {
    JobListComponent
  },
  setup() {
    const jobs = ref<Job[]>([
      { id: "1", title: "Farm worker", location: "Lon Lon Ranch", salary: 30000 },
      { id: "2", title: "Quarryman", location: "Death mountain", salary: 40000 },
      { id: "3", title: "Flute player", location: "The lost woods", salary: 35000 },
      { id: "4", title: "Fisherman", location: "Lake hylia", salary: 21000 },
      { id: "5", title: "Prison guard", location: "Gerudo valley", salary: 32000 }
    ]);

    const order = ref<OrderTerm>("title");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    }

    return {
      jobs,
      handleClick,
      order
    }
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
