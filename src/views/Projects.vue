<script setup lang="ts">
import { ref, onMounted } from 'vue'
import gsap from 'gsap'
import ProjectModal from '../components/ProjectModal.vue'

const selectedProject = ref(null)
const isModalOpen = ref(false)

const projects = [
  {
    title: 'R.A.W: Project',
    description: 'Un jeu d\'horreur en réalité virtuelle développé sous Unity, actuellement en cours de développement. Une expérience immersive qui repousse les limites de l\'horreur en VR.',
    technologies: ['Unity', 'C#', 'VR', 'Game Design', '3D Modeling'],
    status: 'En développement',
    type: 'Jeu VR',
    image: '/raw-project.jpg',
    longDescription: 'R.A.W Project est une expérience horrifique unique en réalité virtuelle. Le jeu plonge les joueurs dans un environnement sombre et oppressant où chaque décision peut avoir des conséquences mortelles. Développé avec Unity, le jeu utilise les dernières technologies VR pour créer une immersion totale.'
  },
  {
    title: 'Projet Mystère',
    description: 'Un projet innovant en cours de développement. Plus d\'informations seront dévoilées prochainement.',
    technologies: ['Coming Soon'],
    status: 'En développement',
    type: 'Coming Soon',
    image: '/mystery-project.jpg'
  },
  {
    title: 'Future Innovation',
    description: 'Un projet secret qui changera la façon dont nous interagissons avec la technologie.',
    technologies: ['Coming Soon'],
    status: 'En développement',
    type: 'Coming Soon',
    image: '/future-project.jpg'
  }
]

const openModal = (project: any) => {
  selectedProject.value = project
  isModalOpen.value = true
}

onMounted(() => {
  gsap.from('.project-card', {
    opacity: 0,
    y: 30,
    duration: 0.8,
    stagger: 0.2,
    ease: 'power2.out'
  })
})
</script>

<template>
  <div class="min-h-screen pt-20 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <h2 class="text-4xl font-bold text-center mb-12 text-indigo-400">
        Mes Projets
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="project in projects"
          :key="project.title"
          class="project-card bg-gray-800/50 backdrop-blur-sm rounded-xl overflow-hidden shadow-xl hover:shadow-indigo-500/20 transition-all duration-300 cursor-pointer"
          @click="openModal(project)"
        >
          <div class="relative h-48">
            <img
              v-if="project.image"
              :src="project.image"
              :alt="project.title"
              class="w-full h-full object-cover"
            />
            <div v-else class="w-full h-full bg-gray-700 flex items-center justify-center">
              <svg class="w-12 h-12 text-gray-500" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" />
              </svg>
            </div>
          </div>
          
          <div class="p-6 space-y-4">
            <div>
              <h3 class="text-xl font-bold text-indigo-300 mb-2">
                {{ project.title }}
              </h3>
              <div class="flex gap-2 mb-4">
                <span class="px-3 py-1 text-sm bg-indigo-600/30 text-indigo-300 rounded-full">
                  {{ project.status }}
                </span>
                <span class="px-3 py-1 text-sm bg-purple-600/30 text-purple-300 rounded-full">
                  {{ project.type }}
                </span>
              </div>
              <p class="text-gray-300 line-clamp-3">
                {{ project.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <ProjectModal
      :is-open="isModalOpen"
      :project="selectedProject"
      @close="isModalOpen = false"
    />
  </div>
</template>