<template>
  <div>
    <Hero />
    <HomeCards />
    <JobListings
      :limit="3"
      :show-button="true"
    />
  </div>
</template>


<script setup>
import Hero from '@/components/Hero.vue'
import HomeCards from '@/components/HomeCards.vue'
import JobListings from '@/components/JobListings.vue'
</script>
