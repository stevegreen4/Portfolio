<script setup>
import TopHeader from '../components/TopHeader.vue'
import PictureRoll from '../components/PictureRoll.vue'
</script>

<template>
  <TopHeader />
  <div class="about">
    <p>
      bio about myself. will include my professional accomplisments, followed by things I do in my free time. 
    </p>
  </div>
  <PictureRoll />
</template>

<style scoped>
.about {
  padding-top: 80px; /* Add padding to account for fixed header */
}
</style>
