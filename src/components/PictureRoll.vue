<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const images = [
  '/IMG_0881.JPG',
  '/IMG_0882.JPG',
  '/IMG_1132.JPG',
  '/IMG_3026.jpg'
]

const currentIndex = ref(0)
let intervalId = null

const nextImage = () => {
  currentIndex.value = (currentIndex.value + 1) % images.length
}

onMounted(() => {
  // Start the automatic slideshow
  intervalId = setInterval(nextImage, 5000)
})

onUnmounted(() => {
  // Clean up the interval when component is destroyed
  if (intervalId) clearInterval(intervalId)
})
</script>

<template>
  <div class="picture-roll">
    <div class="slider-container">
      <transition name="slide">
        <img 
          :key="currentIndex"
          :src="images[currentIndex]" 
          :alt="`Slide ${currentIndex + 1}`"
        >
      </transition>
    </div>
  </div>
</template>

<style scoped>
.picture-roll {
  width: 100%;
  max-width: 800px;
  margin: 0 auto;
  overflow: hidden;
  
}

.slider-container {
  position: relative;
  width: 100%;
  aspect-ratio: 16/9;
  display: flex;
  justify-content: center;
  align-items: center;
}

img {
  position: absolute;
  max-width: 100%;
  max-height: 100%;
  width: auto;
  height: auto;
  object-fit: contain;
}

/* Slide transition effects */
.slide-enter-active,
.slide-leave-active {
  transition: all 0.5s ease;
}

.slide-enter-from {
  transform: translateX(100%);
}

.slide-leave-to {
  transform: translateX(-100%);
}

.slide-enter-to,
.slide-leave-from {
  transform: translateX(0);
}
</style>