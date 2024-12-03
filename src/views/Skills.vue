<script setup lang="ts">
const skillCategories = [
  {
    name: 'Langages',
    skills: ['PHP', 'SQL', 'JavaScript', 'C#']
  },
  {
    name: 'Frameworks & Bibliothèques',
    skills: ['Symfony', 'VueJS', 'TailwindCSS', 'JQuery', 'SCSS']
  },
  {
    name: 'OS',
    skills: ['Windows', 'MacOS', 'Linux']
  },
  {
    name: 'Versionning',
    skills: ['Git', 'GitHub']
  },
  {
    name: 'Virtualisation',
    skills: ['Docker', 'Mamp']
  },
  {
    name: 'IDE',
    skills: ['Visual Studio Code', 'PhpStorm']
  },
  {
    name: 'Game Development',
    skills: ['Unity', 'C#', 'Game Design', '3D Modeling']
  },
  {
    name: 'Divers',
    skills: [
      'DevOps',
      'Éco-conception',
      'WordPress',
      'Référencement Web',
      'Intelligences Artificiels',
      'Unreal Engine',
      'Adobe Suite'
    ]
  }
]
</script>

<template>
  <div class="min-h-screen pt-20 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <h2 class="text-4xl font-bold text-center mb-12 text-indigo-400">
        Compétences
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="category in skillCategories"
          :key="category.name"
          class="bg-gray-800/50 backdrop-blur-sm rounded-xl p-6 shadow-xl hover:shadow-indigo-500/20 transition-all duration-300"
        >
          <h3 class="text-xl font-semibold mb-4 text-indigo-300">
            {{ category.name }}
          </h3>
          <ul class="space-y-3">
            <li
              v-for="skill in category.skills"
              :key="skill"
              class="flex items-center space-x-2 text-gray-300 hover:text-indigo-400 transition-colors duration-200"
            >
              <svg
                class="h-5 w-5 text-indigo-500"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M9 12l2 2 4-4"
                />
              </svg>
              <span>{{ skill }}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>