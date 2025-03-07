<script setup>
import PictureRoll from '../components/PictureRoll.vue'
</script>

<template>
  <div id="about" class="about-section">
    <h2>About Me</h2>
    <p>
      bio about myself. will include my professional accomplisments, followed by things I do in my free time. 
    </p>
    <div class="picture-roll-container">
      <PictureRoll />
    </div>
  </div>
</template>

<style scoped>
.about-section {
  padding: 4rem 2rem;
  text-align: center;
  max-width: 1200px;
  margin: 0 auto;
}

.picture-roll-container {
  width: 100%;
  display: flex;
  justify-content: center;
  margin: 2rem 0;
}

h2 {
  margin-bottom: 2rem;
}

p {
  max-width: 800px;
  margin: 0 auto 3rem;
  line-height: 1.6;
}
</style>
