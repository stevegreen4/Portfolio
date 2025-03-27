<script setup>
import { ref, onMounted } from 'vue'

const projects = ref([])
const loading = ref(true)
const error = ref(null)

// Add projects with their order, display names, and GitHub Pages URLs
const featuredProjects = {
  'Matchas-Marketplace': {
    order: 1,
    displayName: 'Matchas Marketplace',
    pagesUrl: 'https://stevegreen4.github.io/Matchas-Marketplace/'
  },
  'Snake-Game': {
    order: 2,
    displayName: 'Snake Game',
    pagesUrl: 'https://stevegreen4.github.io/Snake-Game/'
  },
  'Game-Backlog-Organizer': {
    order: 3,
    displayName: 'Game Backlog Organizer',
    pagesUrl: 'https://stevegreen4.github.io/Game-Backlog-Organizer/'
  }
}

const fetchProjects = async () => {
  try {
    const response = await fetch('https://api.github.com/users/stevegreen4/repos')
    if (!response.ok) throw new Error('Failed to fetch projects')
    
    const data = await response.json()
    projects.value = data
      .filter(repo => repo.name in featuredProjects)
      .map(repo => ({
        id: repo.id,
        name: featuredProjects[repo.name].displayName,
        repoName: repo.name,
        description: repo.description,
        url: repo.html_url,
        pagesUrl: featuredProjects[repo.name].pagesUrl,
        language: repo.language,
        order: featuredProjects[repo.name].order
      }))
      .sort((a, b) => a.order - b.order)
  } catch (e) {
    error.value = "Sorry there was an error loading my projects. It will be fixed soon."
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchProjects()
})
</script>

<template>
  <div class="projects-container">
    <h2>My Projects</h2>
    
    <div v-if="loading" class="loading">
      Loading projects...
    </div>
    
    <div v-else-if="error" class="error">
      {{ error }}
    </div>
    
    <div v-else class="projects-grid">
      <div v-for="project in projects" 
           :key="project.id" 
           class="project-card">
        <h3>{{ project.name }}</h3>
        <p>{{ project.description || 'No description available' }}</p>
        <div class="project-details">
          <span v-if="project.language" class="language">
            {{ project.language }}
          </span>
        </div>
        <div class="button-container">
          <a :href="project.url" 
             target="_blank" 
             class="view-project">
            View Code
          </a>
          <a :href="project.pagesUrl" 
             target="_blank" 
             class="view-project live-site">
            Live Site
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.projects-container {
  padding: 5rem;
  max-width: 1200px;
  margin: 0 auto;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
  padding: 2rem 0;
}

.project-card {
  background: #1a1a1a;
  border-radius: 8px;
  padding: 1.5rem;
  transition: transform 0.2s;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.project-card:hover {
  transform: translateY(-5px);
}

.project-card h3 {
  margin: 0 0 1rem 0;
  color: #fff;
}

.project-card p {
  color: #ccc;
  margin-bottom: 1rem;
}

.project-details {
  display: flex;
  justify-content: center;
  margin-bottom: 1rem;
  font-size: 0.9rem;
  color: #888;
}

.language {
  padding: 0.25rem 0.75rem;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 4px;
}

.button-container {
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.view-project {
  flex: 1;
  text-align: center;
  padding: 0.5rem 1rem;
  background: #333;
  color: white;
  text-decoration: none;
  border-radius: 4px;
  transition: all 0.2s ease;
}

.view-project.live-site {
  background: #2a6;  /* Different color for live site button */
}

.view-project:hover {
  background: #444;
  transform: translateY(-2px);
}

.view-project.live-site:hover {
  background: #3b7;
}

.loading, .error {
  text-align: center;
  padding: 2rem;
  color: #666;
}

.error {
  color: #ff6b6b;
}
</style>