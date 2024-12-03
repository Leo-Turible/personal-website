<script setup lang="ts">
import { onMounted } from 'vue'
import gsap from 'gsap'

const name = "Léo Turible"
const title = "Développeur Full Stack"
const description = "Passionné par le développement web et les nouvelles technologies, je crée des solutions élégantes et performantes pour répondre aux besoins de mes clients."

onMounted(() => {
  const tl = gsap.timeline()
  tl.from('.hero-text', {
    y: 30,
    opacity: 0,
    duration: 1,
    stagger: 0.2
  })
  .from('.hero-buttons', {
    y: 20,
    opacity: 0,
    duration: 0.8
  }, '-=0.5')
})
</script>

<template>
  <div class="min-h-screen pt-20 flex items-center justify-center px-4 sm:px-6 lg:px-8">
    <div class="text-center max-w-4xl mx-auto">
      <h1 class="hero-text text-5xl sm:text-6xl md:text-7xl font-extrabold mb-8">
        <span class="block text-transparent bg-clip-text bg-gradient-to-r from-indigo-400 to-purple-500">
          Hello, je suis {{ name }}
        </span>
        <span class="block mt-2 text-indigo-300">{{ title }}</span>
      </h1>
      <p class="hero-text mt-6 text-xl text-gray-300 max-w-3xl mx-auto leading-relaxed">
        {{ description }}
      </p>
      <div class="hero-buttons mt-10 flex flex-col sm:flex-row gap-4 justify-center">
        <router-link
          to="/projects"
          class="px-8 py-3 bg-indigo-600 text-white rounded-full font-medium hover:bg-indigo-700 transition-colors duration-300 shadow-lg hover:shadow-indigo-500/50"
        >
          Voir mes projets
        </router-link>
        <router-link
          to="/contact"
          class="px-8 py-3 bg-gray-800 text-white rounded-full font-medium hover:bg-gray-700 transition-colors duration-300 shadow-lg"
        >
          Me contacter
        </router-link>
      </div>
    </div>
  </div>
</template>