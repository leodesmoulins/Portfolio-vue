<template>
  <div class="container-fluid">
    <footer class="fixed bottom-4 left-1/2 transform -translate-x-1/2 w-full max-w-xs sm:max-w-sm md:max-w-md lg:max-w-lg flex justify-center items-center bg-transparent z-50">
      <div class="bg-purple-700 dark:bg-purple-900 shadow-md rounded-xl px-2 py-1 flex space-x-2 sm:space-x-4">
        <button @click="scrollToSection('#home')" :class="buttonClass('#home')">
          <div class="flex flex-col items-center space-y-0.5">
            <HomeIcon class="h-5 w-5" />
            <p class="text-[10px]">Home</p>
          </div>
        </button>
        <button @click="scrollToSection('#about')" :class="buttonClass('#about')">
          <div class="flex flex-col items-center space-y-0.5">
            <UserIcon class="h-5 w-5" />
            <p class="text-[10px]">About</p>
          </div>
        </button>
        <button @click="scrollToSection('#skills')" :class="buttonClass('#skills')">
          <div class="flex flex-col items-center space-y-0.5">
            <BookOpenIcon class="h-5 w-5" />
            <p class="text-[10px]">Skills</p>
          </div>
        </button>
        <button @click="scrollToSection('#project')" :class="buttonClass('#project')">
          <div class="flex flex-col items-center space-y-0.5">
            <BriefcaseIcon class="h-5 w-5" />
            <p class="text-[10px]">Project</p>
          </div>
        </button>
        <button @click="scrollToSection('#contact')" :class="buttonClass('#contact')">
          <div class="flex flex-col items-center space-y-0.5">
            <EnvelopeIcon class="h-5 w-5" />
            <p class="text-[10px]">Contact</p>
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