<template>
  <div :class="{'dark': isDarkMode}" class="min-h-screen flex flex-col">
    <Navbar :isDarkMode="isDarkMode" @toggleMode="toggleMode"/>
    <div class="flex-grow container-fluid mx-auto w-full py-8 px-8 bg-purple-100 dark:bg-gray-900">
      <section id="home" class="min-h-screen flex items-center justify-center">
        <Home />
      </section>
      <section id="about" class="min-h-screen flex items-center justify-center pt-10">
        <About />
      </section>
      <section id="skills" class="min-h-screen flex items-center justify-center pt-10">
        <Skills />
      </section>
      <section id="project" class="min-h-screen flex items-center justify-center pt-10">
        <Project />
      </section>
      <section id="contact" class="min-h-screen flex items-center justify-center pt-10">
        <Contact />
      </section>
    </div>
    <Footer/>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import About from '../components/about.vue'
import Footer from '../components/footer.vue'
import Home from '../components/home.vue'
import Navbar from '../components/navbar.vue'
import Project from '../components/project.vue'
import Skills from '../components/skills.vue'

const isDarkMode = ref(false)

function toggleMode() {
  isDarkMode.value = !isDarkMode.value
  document.documentElement.classList.toggle('dark', isDarkMode.value)
}
</script>