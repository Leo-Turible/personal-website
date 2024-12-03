<script setup lang="ts">
import { defineProps, defineEmits } from 'vue'
import { Dialog, DialogPanel, TransitionChild, TransitionRoot } from '@headlessui/vue'

const props = defineProps<{
  isOpen: boolean
  project: any
}>()

const emit = defineEmits(['close'])

const close = () => {
  emit('close')
}
</script>

<template>
  <TransitionRoot appear :show="isOpen" as="template">
    <Dialog as="div" class="relative z-50" @close="close">
      <TransitionChild
        as="template"
        enter="duration-300 ease-out"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="duration-200 ease-in"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div class="fixed inset-0 bg-black/75" />
      </TransitionChild>

      <div class="fixed inset-0 overflow-y-auto">
        <div class="flex min-h-full items-center justify-center p-4 text-center">
          <TransitionChild
            as="template"
            enter="duration-300 ease-out"
            enter-from="opacity-0 scale-95"
            enter-to="opacity-100 scale-100"
            leave="duration-200 ease-in"
            leave-from="opacity-100 scale-100"
            leave-to="opacity-0 scale-95"
          >
            <DialogPanel class="w-full max-w-2xl transform overflow-hidden rounded-2xl bg-gray-800 p-6 text-left align-middle shadow-xl transition-all">
              <div class="relative">
                <button
                  @click="close"
                  class="absolute right-0 top-0 text-gray-400 hover:text-white"
                >
                  <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                  </svg>
                </button>

                <div class="mt-2">
                  <img
                    v-if="project.image"
                    :src="project.image"
                    :alt="project.title"
                    class="w-full h-64 object-cover rounded-lg mb-6"
                  />
                  
                  <h3 class="text-2xl font-bold text-indigo-400 mb-4">
                    {{ project.title }}
                  </h3>

                  <p class="text-gray-300 mb-6">
                    {{ project.description }}
                  </p>

                  <div class="space-y-4">
                    <div v-if="project.technologies?.length">
                      <h4 class="text-lg font-semibold text-indigo-300 mb-2">Technologies</h4>
                      <div class="flex flex-wrap gap-2">
                        <span
                          v-for="tech in project.technologies"
                          :key="tech"
                          class="px-3 py-1 text-sm bg-gray-700 text-gray-300 rounded-full"
                        >
                          {{ tech }}
                        </span>
                      </div>
                    </div>

                    <div v-if="project.link" class="mt-6">
                      <a
                        :href="project.link"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="inline-flex items-center px-4 py-2 bg-indigo-600 text-white rounded-lg hover:bg-indigo-700 transition-colors duration-200"
                      >
                        <span>Voir le projet</span>
                        <svg
                          class="ml-2 h-4 w-4"
                          fill="none"
                          viewBox="0 0 24 24"
                          stroke="currentColor"
                        >
                          <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"
                          />
                        </svg>
                      </a>
                    </div>
                  </div>
                </div>
              </div>
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>