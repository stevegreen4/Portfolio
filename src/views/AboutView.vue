<script setup>
import TopHeader from '../components/TopHeader.vue'
</script>

<template>
  <TopHeader />
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<style scoped>
.about {
  padding-top: 80px; /* Add padding to account for fixed header */
}
</style>
