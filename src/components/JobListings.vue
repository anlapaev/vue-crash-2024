<template>
  <div>
    <section class="bg-blue-50 px-4 py-10">
      <div class="container-xl lg:container m-auto">
        <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
          Browse Jobs
        </h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <JobListing
            v-for="job in jobs.slice(0, props.limit || jobs.length)"
            :key="job.id"
            class="w-full"
            :job="job"
          />
        </div>
      </div>
    </section>
    <section
      v-if="props.showButton"
      class="m-auto max-w-lg my-10 px-6"
    >
      <RouterLink
        to="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
      >
        View All Jobs
      </RouterLink>
    </section>
  </div>
</template>

<script setup>
import JobListing from '@/components/JobListing.vue'
import { RouterLink } from 'vue-router'
import { ref, defineProps, onMounted } from 'vue'
import axios from 'axios'

const jobs = ref([])
const props = defineProps({
  limit: Number,
  showButton: {
    type: Boolean,
    default: false
  }
})

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost:8000/jobs')
    jobs.value = response.data
  } catch (error) {
    console.log(error)
  }
})
</script>
