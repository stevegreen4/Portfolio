<script setup>
import { ref } from 'vue'

const activeSection = ref(null)

const toggleSection = (section) => {
  activeSection.value = activeSection.value === section ? null : section
}
</script>

<template>
    <div class="skills-container">
        <h2 class="main-title">Other Skills</h2>
        <p class="main-description">
            Outside of software development I have multiple years of experience in several other industries. Check out all of the work I have done. 
        </p>
        
        <div class="sections-container">
            <div class="section">
                <h3 @click="toggleSection('events')" 
                    :class="{ active: activeSection === 'events' }">
                    Event Management
                </h3>
                <transition name="fade">
                    <div v-if="activeSection === 'events'" class="section-content">
                        <p>
                            Resume list of skills from events 
                        </p>
                        <img src="" alt="Events worked">
                    </div>
                </transition>
            </div>

            <div class="section">
                <h3 @click="toggleSection('customer')"
                    :class="{ active: activeSection === 'customer' }">
                    Customer Service
                </h3>
                <transition name="fade">
                    <div v-if="activeSection === 'customer'" class="section-content">
                        <p>
                            Resume list of skills from customer service 
                        </p>
                        <img src="" alt="Spectrum machine logo">
                    </div>
                </transition>
            </div>
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
    display: flex;
    justify-content: center;
    gap: 4rem;
    margin-top: 2rem;
    position: relative;
}

.section {
    flex: 1;
    max-width: 400px;
}

.section h3 {
    cursor: pointer;
    padding: 1rem;
    margin: 0;
    border-radius: 8px;
    transition: all 0.3s ease;
}

.section h3:hover {
    background-color: rgba(255, 255, 255, 0.1);
}

.section h3.active {
    background-color: rgba(255, 255, 255, 0.15);
}

.section-content {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 100%;
    max-width: 800px;
    margin-top: 2rem;
    padding: 1rem;
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
    .sections-container {
        flex-direction: column;
        align-items: center;
        gap: 2rem;
    }

    .section {
        width: 100%;
    }

    .section-content {
        position: static;
        transform: none;
        margin-top: 1rem;
    }
}
</style>