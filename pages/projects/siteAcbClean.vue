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
          <h3 class="text-xl font-bold text-purple-700 dark:text-purple-300">Acbclean</h3>
          <p class="text-lg text-gray-700 dark:text-gray-300 mt-4">
            Acbclean est une entreprise de nettoyage de locaux professionnels et particuliers. Durant ma première année de BTS SIO j'ai du faire un stage de 5 semaine.
            J'ai donc choisi de faire mon stage chez Acbclean pour pouvoir mettre en pratique mes compétences en développement web.
            J'ai réalisé un site web pour cette entreprise, qui permet de présenter les services proposés, les tarifs, les avis clients et un formulaire de contact.
          </p>
          <p class="text-lg text-gray-700 dark:text-gray-300 mt-4">
            J'ai utilisé les technologies HTML, CSS et JavaScript pour réaliser ce projet. J'ai également utilisé Figma pour créer le design du site.
            Je me suis occupé de l'hébergement du site et de son référencement sur les moteurs de recherche.
            j'ai utilisé OVHCloud pour le nom de domaine et ensuite Vercel pour l'hébergement du site.
          </p>
        </div>
      </div>

      <!-- Carte avec les technologies utilisées -->
      <div class="mb-12">
        <h2 class="text-2xl font-semibold text-purple-700 dark:text-purple-300 mb-4">Technologies utilisées</h2>
        <div class="border border-purple-800 p-8 rounded-lg shadow-md bg-purple-200 dark:bg-gray-900">
          <div class="flex flex-wrap justify-center space-x-4">
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 32 32"><path fill="#f5de19" d="M2 2h28v28H2z"/><path d="M20.809 23.875a2.87 2.87 0 0 0 2.6 1.6c1.09 0 1.787-.545 1.787-1.3c0-.9-.716-1.222-1.916-1.747l-.658-.282c-1.9-.809-3.16-1.822-3.16-3.964c0-1.973 1.5-3.476 3.853-3.476a3.89 3.89 0 0 1 3.742 2.107L25 18.128A1.79 1.79 0 0 0 23.311 17a1.145 1.145 0 0 0-1.259 1.128c0 .789.489 1.109 1.618 1.6l.658.282c2.236.959 3.5 1.936 3.5 4.133c0 2.369-1.861 3.667-4.36 3.667a5.06 5.06 0 0 1-4.795-2.691Zm-9.295.228c.413.733.789 1.353 1.693 1.353c.864 0 1.41-.338 1.41-1.653v-8.947h2.631v8.982c0 2.724-1.6 3.964-3.929 3.964a4.085 4.085 0 0 1-3.947-2.4Z"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">JS</span>
            </div>
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 128 128"><path fill="#1572b6" d="M18.814 114.123L8.76 1.352h110.48l-10.064 112.754l-45.243 12.543z"/><path fill="#33a9dc" d="m64.001 117.062l36.559-10.136l8.601-96.354h-45.16z"/><path fill="#fff" d="M64.001 51.429h18.302l1.264-14.163H64.001V23.435h34.682l-.332 3.711l-3.4 38.114h-30.95z"/><path fill="#ebebeb" d="m64.083 87.349l-.061.018l-15.403-4.159l-.985-11.031H33.752l1.937 21.717l28.331 7.863l.063-.018z"/><path fill="#fff" d="m81.127 64.675l-1.666 18.522l-15.426 4.164v14.39l28.354-7.858l.208-2.337l2.406-26.881z"/><path fill="#ebebeb" d="M64.048 23.435v13.831H30.64l-.277-3.108l-.63-7.012l-.331-3.711zm-.047 27.996v13.831H48.792l-.277-3.108l-.631-7.012l-.33-3.711z"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">CSS</span>
            </div>
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 32 32"><path fill="#e44f26" d="M5.902 27.201L3.655 2h24.69l-2.25 25.197L15.985 30z"/><path fill="#f1662a" d="m16 27.858l8.17-2.265l1.922-21.532H16z"/><path fill="#ebebeb" d="M16 13.407h-4.09l-.282-3.165H16V7.151H8.25l.074.83l.759 8.517H16zm0 8.027l-.014.004l-3.442-.929l-.22-2.465H9.221l.433 4.852l6.332 1.758l.014-.004z"/><path fill="#fff" d="M15.989 13.407v3.091h3.806l-.358 4.009l-3.448.93v3.216l6.337-1.757l.046-.522l.726-8.137l.076-.83zm0-6.256v3.091h7.466l.062-.694l.141-1.567l.074-.83z"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">HTML</span>
            </div>  
            <div class="flex flex-col items-center">
                <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 128 128"><path fill="#0acf83" d="M45.5 129c11.9 0 21.5-9.6 21.5-21.5V86H45.5C33.6 86 24 95.6 24 107.5S33.6 129 45.5 129m0 0"/><path fill="#a259ff" d="M24 64.5C24 52.6 33.6 43 45.5 43H67v43H45.5C33.6 86 24 76.4 24 64.5m0 0"/><path fill="#f24e1e" d="M24 21.5C24 9.6 33.6 0 45.5 0H67v43H45.5C33.6 43 24 33.4 24 21.5m0 0"/><path fill="#ff7262" d="M67 0h21.5C100.4 0 110 9.6 110 21.5S100.4 43 88.5 43H67zm0 0"/><path fill="#1abcfe" d="M110 64.5c0 11.9-9.6 21.5-21.5 21.5S67 76.4 67 64.5S76.6 43 88.5 43S110 52.6 110 64.5m0 0"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">Figma</span>
            </div>
            <!-- Ajoutez d'autres icônes de technologies ici -->
          </div>
        </div>
      </div>

      <!-- Boutons pour diriger vers le projet en ligne et le prochain projet -->
      <div class="flex justify-between">
        <a href="https://www.acbclean.fr" target="_blank" class="bg-purple-700 text-white py-2 px-4 rounded hover:bg-purple-600">
          Voir le projet en ligne
        </a>
        <NuxtLink to="/projects/OldPortfolio" class="bg-purple-700 hover:underline text-white py-2 px-4 rounded hover:bg-purple-600">
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
  "/img/img_acbclean.png"
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
