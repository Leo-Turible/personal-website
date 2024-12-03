<script setup lang="ts">
import { ref, onMounted } from 'vue'
import gsap from 'gsap'

const name = ref('')
const email = ref('')
const phone = ref('')
const message = ref('')

const handleSubmit = () => {
  console.log({ 
    name: name.value, 
    email: email.value, 
    phone: phone.value, 
    message: message.value 
  })
}

onMounted(() => {
  gsap.from('.contact-form', {
    opacity: 0,
    y: 30,
    duration: 0.8,
    ease: 'power2.out'
  })
})

const contactInfo = [
  {
    icon: 'M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75',
    title: 'Email',
    value: 'turibleleo@gmail.com',
    href: 'mailto:turibleleo@gmail.com'
  },
  {
    icon: 'M9 6.75V15m6-6v8.25m.375 0c.375 0 .375.375 0 .375H15V15.75m-4.5-4.5v8.25m.375 0c.375 0 .375.375 0 .375H9.75v-9',
    title: 'LinkedIn',
    value: '/in/leoturible',
    href: 'https://www.linkedin.com/in/leoturible/'
  },
  {
    icon: 'M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253m0 0A17.919 17.919 0 0112 16.5c-3.162 0-6.133-.815-8.716-2.247m0 0A9.015 9.015 0 013 12c0-1.605.42-3.113 1.157-4.418',
    title: 'Site Web',
    value: 'leoturible.fr',
    href: 'https://leoturible.fr'
  }
]
</script>

<template>
  <div class="min-h-screen pt-20 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <h2 class="text-4xl font-bold text-center mb-12 text-indigo-400">
        Contact
      </h2>
      
      <div class="grid md:grid-cols-2 gap-12">
        <!-- Contact Info -->
        <div class="space-y-8">
          <h3 class="text-2xl font-semibold text-indigo-300 mb-6">
            Mes coordonnées
          </h3>
          <div class="space-y-6">
            <div
              v-for="info in contactInfo"
              :key="info.title"
              class="flex items-start space-x-4 bg-gray-800/30 backdrop-blur-sm p-4 rounded-xl hover:bg-gray-800/50 transition-colors duration-200"
            >
              <svg
                class="w-6 h-6 text-indigo-400 mt-1 flex-shrink-0"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  :d="info.icon"
                />
              </svg>
              <div>
                <h4 class="text-lg font-medium text-indigo-300">{{ info.title }}</h4>
                <a 
                  :href="info.href"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-gray-300 hover:text-indigo-400 transition-colors duration-200"
                >
                  {{ info.value }}
                </a>
              </div>
            </div>
          </div>

          <!-- CV Download Button -->
          <a
            href="/cv.pdf"
            download
            class="inline-flex items-center px-6 py-3 bg-indigo-600 text-white rounded-lg font-medium hover:bg-indigo-700 transition-colors duration-300 shadow-lg hover:shadow-indigo-500/50 w-full justify-center space-x-2"
          >
            <svg
              class="w-5 h-5"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"
              />
            </svg>
            <span>Télécharger mon CV</span>
          </a>
        </div>

        <!-- Contact Form -->
        <div class="contact-form bg-gray-800/50 backdrop-blur-sm rounded-xl p-8 shadow-xl">
          <h3 class="text-2xl font-semibold text-indigo-300 mb-6">
            Envoyez-moi un message
          </h3>
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <div>
              <label
                for="name"
                class="block text-sm font-medium text-gray-300 mb-2"
              >
                Nom complet
              </label>
              <input
                type="text"
                id="name"
                v-model="name"
                required
                class="w-full px-4 py-2 bg-gray-700/50 border border-gray-600 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-transparent text-gray-300 placeholder-gray-500"
                placeholder="Votre nom complet"
              />
            </div>
            <div>
              <label
                for="email"
                class="block text-sm font-medium text-gray-300 mb-2"
              >
                Email
              </label>
              <input
                type="email"
                id="email"
                v-model="email"
                required
                class="w-full px-4 py-2 bg-gray-700/50 border border-gray-600 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-transparent text-gray-300 placeholder-gray-500"
                placeholder="votre@email.com"
              />
            </div>
            <div>
              <label
                for="phone"
                class="block text-sm font-medium text-gray-300 mb-2"
              >
                Téléphone
              </label>
              <input
                type="tel"
                id="phone"
                v-model="phone"
                class="w-full px-4 py-2 bg-gray-700/50 border border-gray-600 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-transparent text-gray-300 placeholder-gray-500"
                placeholder="Votre numéro de téléphone"
              />
            </div>
            <div>
              <label
                for="message"
                class="block text-sm font-medium text-gray-300 mb-2"
              >
                Message
              </label>
              <textarea
                id="message"
                v-model="message"
                rows="4"
                required
                class="w-full px-4 py-2 bg-gray-700/50 border border-gray-600 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-transparent text-gray-300 placeholder-gray-500"
                placeholder="Votre message..."
              ></textarea>
            </div>
            <button
              type="submit"
              class="w-full px-6 py-3 bg-indigo-600 text-white rounded-lg font-medium hover:bg-indigo-700 transition-colors duration-300 shadow-lg hover:shadow-indigo-500/50"
            >
              Envoyer
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>