<script setup>
import { ref } from 'vue'
import HelloSlider from '../components/HelloSlider.vue'
import TopHeader from '../components/TopHeader.vue'
import ProjectCards from '../components/SoftwareProjects.vue'
import SkillsSection from '../components/SkillsHeader.vue'
import IntroBlock from '../components/IntroBlock.vue'
import AboutSection from '../components/AboutSection.vue'


const showContent = ref(false)

const handleAnimationComplete = () => {
  showContent.value = true
}
</script>

<template>
  <HelloSlider @animation-complete="handleAnimationComplete" />
  <Transition name="fade">
    <div v-if="showContent" class="content-wrapper">
      <TopHeader />
      <main>
        <IntroBlock />
        
        <SkillsSection />
        <AboutSection />
      </main>
    </div>
  </Transition>
</template>

<style scoped>
.content-wrapper {
  width: 100%;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>