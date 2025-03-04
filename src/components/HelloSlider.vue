<script setup>
import { onMounted, ref } from 'vue'

const intro = ref(null)
const logoSpans = ref([])
const emit = defineEmits(['animationComplete'])

onMounted(() => {
  // Get all logo spans after component is mounted
  logoSpans.value = Array.from(document.querySelectorAll('.logo'))
  
  setTimeout(() => {
    // Animation for span elements in 'logo-header'
    logoSpans.value.forEach((span, index) => {
      setTimeout(() => {
        span.classList.add('active')
      }, (index + 1) * 400)
    })

    // Remove active class, add the fade animation to span elements
    setTimeout(() => {
      logoSpans.value.forEach((span, index) => {
        setTimeout(() => {
          span.classList.remove('active')
          span.classList.add('fade')
        }, (index + 1) * 50)
      })
    }, 2000)

    // Animation for entire intro class/splash screen
    setTimeout(() => {
      intro.value.style.top = '-100vh'
      // Emit event after animation is complete
      setTimeout(() => {
        emit('animationComplete')
      }, 1000) // Wait for slide-up animation to complete
    }, 2300)
  })
})
</script>

<template>
  <div class="intro" ref="intro">
    <h1 class="logo-header">
      <span class="logo">Steve </span>
      <span class="logo">Green</span>
    </h1>
  </div>
</template>

<style scoped>
    .intro {
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    background-color: black;
    transition: 1s;
}

.logo-header {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
}

.logo {
    position: relative;
    display: inline-block;
    bottom: -20px;
    opacity: 0;
}

.logo.active {
    bottom: 0;
    opacity: 1;
    transition: ease-in-out .5s;
}

.logo.fade {
    bottom: 150px;
    opacity: 0;
    transition: ease-in-out .5s;
}
</style>
