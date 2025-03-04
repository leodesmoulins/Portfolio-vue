<template>
  <div class="container-fluid">
    <footer class="fixed bottom-0 left-0 w-full flex justify-center items-center py-4 bg-transparent">
      <div class="bg-purple-700 dark:bg-purple-900 shadow-md rounded-4xl p-4 flex space-x-4">
        <button @click="scrollToSection('#home')" :class="buttonClass('#home')">
          <div class="flex flex-col items-center space-y-1">
            <HomeIcon class="h-6 w-6" />
            <p class="text-xs">Home</p>
          </div>
        </button>
        <button @click="scrollToSection('#about')" :class="buttonClass('#about')">
          <div class="flex flex-col items-center space-y-1">
            <UserIcon class="h-6 w-6" />
            <p class="text-xs">About</p>
          </div>
        </button>
        <button @click="scrollToSection('#skills')" :class="buttonClass('#skills')">
          <div class="flex flex-col items-center space-y-1">
            <BookOpenIcon class="h-6 w-6" />
            <p class="text-xs">Skills</p>
          </div>
        </button>
        <button @click="scrollToSection('#project')" :class="buttonClass('#project')">
          <div class="flex flex-col items-center space-y-1">
            <BriefcaseIcon class="h-6 w-6" />
            <p class="text-xs">Project</p>
          </div>
        </button>
        <button @click="scrollToSection('#contact')" :class="buttonClass('#contact')">
          <div class="flex flex-col items-center space-y-1">
            <EnvelopeIcon class="h-6 w-6" />
            <p class="text-xs">Contact</p>
          </div>
        </button>
      </div>
    </footer>
  </div>
</template>

<script lang="ts" setup>
import { ref, onMounted } from 'vue'
import { gsap } from 'gsap'
import { ScrollToPlugin } from 'gsap/ScrollToPlugin'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { HomeIcon, UserIcon, BookOpenIcon, BriefcaseIcon, EnvelopeIcon } from '@heroicons/vue/24/outline'

gsap.registerPlugin(ScrollToPlugin, ScrollTrigger)

const activeSection = ref('#home')

const scrollToSection = (id: string) => {
  gsap.to(window, { duration: 1, scrollTo: id })
}

const buttonClass = (id: string) => {
  return activeSection.value === id
    ? 'px-4 py-2 text-purple-100 dark:text-purple-100 font-bold rounded-4xl bg-purple-800 dark:bg-purple-600 transition duration-300 ease-in-out'
    : 'px-4 py-2 text-purple-100 dark:text-purple-100 font-bold rounded-4xl hover:bg-purple-800 dark:hover:bg-purple-600 transition duration-300 ease-in-out'
}

onMounted(() => {
  const sections = ['#home', '#about', '#skills', '#project', '#contact']
  sections.forEach(section => {
    ScrollTrigger.create({
      trigger: section,
      start: 'top center',
      end: 'bottom center',
      onEnter: () => activeSection.value = section,
      onEnterBack: () => activeSection.value = section,
    })
  })
})
</script>

<style scoped>
/* Ajoutez ici des styles supplémentaires si nécessaire */
</style>