<template>
    <div :class="{'dark': isDarkMode}" class="min-h-screen flex flex-col">
    <Navbar :isDarkMode="isDarkMode" @toggleMode="toggleMode"/>
    <div class="flex-grow container-fluid mx-auto w-full py-8 px-8 bg-purple-100 dark:bg-gray-900">
      
      <!-- Bouton de retour -->
      <div class="mb-8 mt-19">
        <NuxtLink to="/">Retour</NuxtLink>
      </div>

      <!-- Carousel pour les images du projet -->
      <div class="mb-12">
        <h2 class="text-2xl font-semibold text-purple-700 dark:text-purple-300 mb-4">Galerie d'images</h2>
        
        <!-- Carousel Container (horizontal scrolling) -->
        <div class="carousel-container overflow-x-auto flex space-x-4">
          <div 
            v-for="(src, index) in imgs" 
            :key="index" 
            @click="() => showImg(index)"
            class="carousel-item w-64 h-64 rounded-lg shadow-md cursor-pointer"
          >
            <img :src="src" class="w-full h-full object-cover rounded-lg" />
          </div>
        </div>
        <VueEasyLightbox :visible="visibleRef" :imgs="imgs" :index="indexRef" @hide="onHide"/>
      </div>

      <div class="mb-12">
        <h2 class="text-2xl font-semibold text-purple-700 dark:text-purple-300 mb-4">Description du projet</h2>
        <div class="border border-purple-800 p-8 rounded-lg shadow-md bg-purple-200 dark:bg-gray-900">
          <h3 class="text-xl font-bold text-purple-700 dark:text-purple-300">Quinconce Jeune</h3>
          <p class="text-lg text-gray-700 dark:text-gray-300 mt-4">
            Ce projet fictif à été réalisé dans le cadre de ma formation BTS SIO. J'ai du réaliser un site qui va répertorié plusieurs évenements des quiconces aux mans.
            Ce site va permettre aux jeunes de la ville de voir les événements à venir et de s'inscrire à ces derniers. J'ai du réaliser ce site avec le CMS webflow.
            Evidemment il n'est pas destiné a être en ligne mais à être présenté lors de mon examen de BTS.
          </p>
        </div>
      </div>

      <!-- Carte avec les technologies utilisées -->
      <div class="mb-12">
        <h2 class="text-2xl font-semibold text-purple-700 dark:text-purple-300 mb-4">Technologies utilisées</h2>
        <div class="border border-purple-800 p-8 rounded-lg shadow-md bg-purple-200 dark:bg-gray-900">
          <div class="flex flex-wrap justify-center space-x-4">
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 256 256"><g fill="none"><rect width="256" height="256" fill="#4353ff" rx="60"/><path fill="#fff" d="M169.105 103.436s-13.815 43.282-14.836 46.957c-.408-3.607-10.48-81.393-10.48-81.393c-23.547 0-36.069 16.741-42.739 34.436c0 0-16.809 43.418-18.17 47.025c-.068-3.403-2.586-46.617-2.586-46.617C78.864 82.134 59.06 69 43 69l19.328 117.802c24.635-.068 37.906-16.741 44.847-34.503c0 0 14.768-38.315 15.381-40.016c.136 1.633 10.616 74.519 10.616 74.519c24.704 0 38.043-15.584 45.188-32.666L213 69c-24.432 0-37.294 16.673-43.895 34.436"/></g></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">Webflow</span>
            </div>
            
            <!-- Ajoutez d'autres icônes de technologies ici -->
          </div>
        </div>
      </div>

      <!-- Boutons pour diriger vers le projet en ligne et le prochain projet -->
      <div class="flex justify-between">
        <a href="https://quinconces-jeunes.webflow.io" target="_blank" class="bg-purple-700 text-white py-2 px-4 rounded hover:bg-purple-600">
          Voir le projet en ligne
        </a>
        <NuxtLink to="/projects/siteAcbClean" class="bg-purple-700 hover:underline text-white py-2 px-4 rounded hover:bg-purple-600">
          Projet suivant
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import VueEasyLightbox from 'vue-easy-lightbox'

const isDarkMode = ref(false);
const visibleRef = ref(false);
const indexRef = ref(0);

function toggleMode() {
  isDarkMode.value = !isDarkMode.value
  document.documentElement.classList.toggle('dark', isDarkMode.value)
}

const imgs = [
  "/img/img_webflow.PNG"
];

const showImg = (index: any) => {
  indexRef.value = index;
  visibleRef.value = true;
}
const onHide = () => (visibleRef.value = false);



</script>

<style scoped>
.carousel-container {
  display: flex;
  overflow-x: auto;
  gap: 16px;
}

.carousel-item {
  flex-shrink: 0;
  width: 200px; /* Ajuste la taille des images selon tes besoins */
  height: 200px;
}

.carousel-container::-webkit-scrollbar {
  height: 8px;
}

.carousel-container::-webkit-scrollbar-thumb {
  background-color: #aaa;
  border-radius: 10px;
}

.carousel-container::-webkit-scrollbar-track {
  background-color: #f1f1f1;
}
</style>
