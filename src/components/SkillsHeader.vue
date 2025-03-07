<script setup>
import { ref } from 'vue'
import SoftwareProjects from './SoftwareProjects.vue'
import EventSkills from './EventSkills.vue'
import CustomerSkills from './CustomerSkills.vue'

// Set initial value to 'software' to show it by default
const activeSection = ref('software')

const toggleSection = (section) => {
  activeSection.value = activeSection.value === section ? null : section
}
</script>

<template>
    <div class="skills-container">
        <h1 class="main-title">Professional Skills</h1>
        <p class="main-description">
            Check out all of the work I have done.
        </p>
        
        <div class="sections-container">
            <div class="headers">
                <h3 @click="toggleSection('software')" 
                    :class="{ active: activeSection === 'software' }">
                    Software Development
                </h3>
                <h3 @click="toggleSection('events')"
                    :class="{ active: activeSection === 'events' }">
                    Event Management
                </h3>
                <h3 @click="toggleSection('customer')"
                    :class="{ active: activeSection === 'customer' }">
                    Customer Service
                </h3>
            </div>

            <transition name="fade">
                <div v-if="activeSection === 'software'" class="section-content">
                    <SoftwareProjects />
                </div>
                <div v-else-if="activeSection === 'events'" class="section-content">
                    <EventSkills />
                </div>
                <div v-else-if="activeSection === 'customer'" class="section-content">
                    <CustomerSkills />
                </div>
            </transition>
        </div>
    </div>
</template>

<style scoped>
.skills-container {
    padding: 2rem;
    text-align: center;
}

.main-title {
    margin-bottom: 1rem;
}

.main-description {
    max-width: 800px;
    margin: 0 auto 2rem;
}

.sections-container {
    position: relative;
    min-height: 500px;
}

.headers {
    display: flex;
    justify-content: center;
    gap: 4rem;
    margin-bottom: 2rem;
}

h3 {
    cursor: pointer;
    padding: 1rem 2rem;
    margin: 0;
    border-radius: 8px;
    transition: all 0.3s ease;
}

h3:hover {
    background-color: rgba(255, 255, 255, 0.1);
}

h3.active {
    background-color: rgba(255, 255, 255, 0.15);
}

.section-content {
    position: relative;
    left: 0;
    transform: none;
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
}

/* Transition animations */
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}

/* Responsive design */
@media (max-width: 768px) {
    .headers {
        flex-direction: column;
        gap: 1rem;
    }

    .section-content {
        position: static;
        transform: none;
    }
}
</style>