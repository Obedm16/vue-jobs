<template>
  <!-- <h1>Vue Jobs</h1> -->
   <Navbar />
   <RouterView />
   <!-- <Hero title="Test Title" subtitle="Test"/> -->
   <!-- <Hero />
   <HomeCard />
   <JobListing :limit="3" :showButton="true" /> -->
</template>

<script setup>
import Navbar from '@/components/Navbar.vue';
import { RouterView } from 'vue-router';
// import Hero from '@/components/Hero.vue';
// import HomeCard from '@/components/HomeCard.vue';
// import JobListing from '@/components/JobListings.vue';


</script>

<style>

</style>