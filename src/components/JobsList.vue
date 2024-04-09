<script setup lang="ts">
import { computed, type PropType } from 'vue'
import type Job from '@/types/Job'
import type OrderTerm from '@/types/OrderTerm'
// Define props
const props = defineProps({
  jobs: {
    type: Array as PropType<Job[]>,
    required: true
  },
  order: {
    type: String as PropType<OrderTerm>,
    required: true
  }
})
// Using types inside computed
const sortJobs = computed(() => {
  return [...props.jobs].sort((a: Job, b: Job) => a[props.order] > b[props.order] ? 1 : -1)
})
</script>

<template>
  <div>
    <p>Order by {{ order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="job in sortJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">${{ job.salary }}</div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. A, animi assumenda autem beatae blanditiis dicta
            dolore, in ipsum laboriosam modi nihil nobis odio quod rerum sunt tempore vel vero vitae.
          </p>
        </div>
      </li>
    </transition-group>
  </div>
</template>

<style lang="scss" scoped>
.list-move {
  transition: all 1s ease;
}

ul {
  margin: 0;
  padding: 0;
  min-width: 80vw;
}

li {
  list-style: none;
  background: bisque;
  border-radius: 4px;
  padding: 20px;
  margin: 20px 0;
}

.salary {
  color: green;
}
</style>