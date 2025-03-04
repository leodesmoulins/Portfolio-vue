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
          <h3 class="text-xl font-bold text-purple-700 dark:text-purple-300">Hijobs</h3>
          <p class="text-lg text-gray-700 dark:text-gray-300 mt-4">
            C'est un projet réalisé dans le cadre de ma formation BTS SIO durant ma deuxième année. L'objectif était de réalisé
            un site qui permet aux étudiants de trouver des jobs étudiants ou des stages.
            Il y aura plusieurs fonctionnalité et espaces disponibles pour les étudiants et les entreprises ou particuliers.
            Chaque espace à ces droit et fonctionnalité. Ce qui permet a chacun de trouver ce qu'il recherche.
          </p>
          <p class="text-lg text-gray-700 dark:text-gray-300 mt-4">
            Un étudiant va pouvoir chercher des jobs ou stage tandis que les entreprise et particulier vont posté des annonces pour chercher des étudiants.
          </p>
        </div>
      </div>

      <!-- Carte avec les technologies utilisées -->
      <div class="mb-12">
        <h2 class="text-2xl font-semibold text-purple-700 dark:text-purple-300 mb-4">Technologies utilisées</h2>
        <div class="border border-purple-800 p-8 rounded-lg shadow-md bg-purple-200 dark:bg-gray-900">
          <div class="flex flex-wrap justify-center space-x-4">
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 256 135"><defs><radialGradient id="logosPhp0" cx=".837" cy="-125.811" r="363.057" gradientTransform="translate(76.464 81.918)scale(.463)" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#fff"/><stop offset=".5" stop-color="#4c6b97"/><stop offset="1" stop-color="#231f20"/></radialGradient></defs><ellipse cx="128" cy="67.3" fill="url(#logosPhp0)" rx="128" ry="67.3"/><ellipse cx="128" cy="67.3" fill="#6181b6" rx="123" ry="62.3"/><path fill="#fff" d="m152.9 87.5l6.1-31.4c1.4-7.1.2-12.4-3.4-15.7c-3.5-3.2-9.5-4.8-18.3-4.8h-10.6l3-15.6c.1-.6 0-1.2-.4-1.7s-.9-.7-1.5-.7h-14.6c-1 0-1.8.7-2 1.6l-6.5 33.3c-.6-3.8-2-7-4.4-9.6c-4.3-4.9-11-7.4-20.1-7.4H52.1c-1 0-1.8.7-2 1.6L37 104.7c-.1.6 0 1.2.4 1.7s.9.7 1.5.7h14.7c1 0 1.8-.7 2-1.6l3.2-16.3h10.9c5.7 0 10.6-.6 14.3-1.8q5.85-1.95 10.5-6.3c2.5-2.3 4.6-4.9 6.2-7.7l-2.6 13.5c-.1.6 0 1.2.4 1.7s.9.7 1.5.7h14.6c1 0 1.8-.7 2-1.6l7.2-37h10c4.3 0 5.5.8 5.9 1.2c.3.3.9 1.5.2 5.2L134.1 87c-.1.6 0 1.2.4 1.7s.9.7 1.5.7h15c.9-.3 1.7-1 1.9-1.9m-67.6-26c-.9 4.7-2.6 8.1-5.1 10s-6.6 2.9-12 2.9h-6.5l4.7-24.2h8.4c6.2 0 8.7 1.3 9.7 2.4c1.3 1.6 1.6 4.7.8 8.9m130-18.6c-4.3-4.9-11-7.4-20.1-7.4h-28.3c-1 0-1.8.7-2 1.6l-13.1 67.5c-.1.6 0 1.2.4 1.7s.9.7 1.5.7h14.7c1 0 1.8-.7 2-1.6l3.2-16.3h10.9c5.7 0 10.6-.6 14.3-1.8q5.85-1.95 10.5-6.3c2.6-2.4 4.8-5.1 6.4-8s2.8-6.1 3.5-9.6c1.7-8.7.4-15.5-3.9-20.5M200 61.5c-.9 4.7-2.6 8.1-5.1 10s-6.6 2.9-12 2.9h-6.5l4.7-24.2h8.4c6.2 0 8.7 1.3 9.7 2.4c1.4 1.6 1.7 4.7.8 8.9"/><path fill="#000004" d="M74.8 48.2c5.6 0 9.3 1 11.2 3.1s2.3 5.6 1.3 10.6c-1 5.2-3 9-5.9 11.2q-4.35 3.3-13.2 3.3h-8.9l5.5-28.2zM39 105h14.7l3.5-17.9h12.6c5.6 0 10.1-.6 13.7-1.8s6.8-3.1 9.8-5.9q3.75-3.45 6-7.5c1.5-2.7 2.6-5.7 3.2-9c1.6-8 .4-14.2-3.5-18.7s-10.1-6.7-18.6-6.7H52.1zm74.3-85.4h14.6l-3.5 17.9h13c8.2 0 13.8 1.4 16.9 4.3s4 7.5 2.8 13.9L151 87.1h-14.8l5.8-29.9c.7-3.4.4-5.7-.7-6.9s-3.6-1.9-7.3-1.9h-11.7l-7.5 38.7h-14.6zm76.2 28.6c5.6 0 9.3 1 11.2 3.1s2.3 5.6 1.3 10.6c-1 5.2-3 9-5.9 11.2q-4.35 3.3-13.2 3.3H174l5.5-28.2zM153.7 105h14.7l3.5-17.9h12.6c5.6 0 10.1-.6 13.7-1.8s6.8-3.1 9.8-5.9q3.75-3.45 6-7.5c1.5-2.7 2.6-5.7 3.2-9c1.6-8 .4-14.2-3.5-18.7s-10.1-6.7-18.6-6.7h-28.3z"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">PHP</span>
            </div>
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 32 32"><path fill="#44a8b3" d="M9 13.7q1.4-5.6 7-5.6c5.6 0 6.3 4.2 9.1 4.9q2.8.7 4.9-2.1q-1.4 5.6-7 5.6c-5.6 0-6.3-4.2-9.1-4.9q-2.8-.7-4.9 2.1m-7 8.4q1.4-5.6 7-5.6c5.6 0 6.3 4.2 9.1 4.9q2.8.7 4.9-2.1q-1.4 5.6-7 5.6c-5.6 0-6.3-4.2-9.1-4.9q-2.8-.7-4.9 2.1"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">Tailwind CSS</span>
            </div>
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 32 32"><path fill="#e44f26" d="M5.902 27.201L3.655 2h24.69l-2.25 25.197L15.985 30z"/><path fill="#f1662a" d="m16 27.858l8.17-2.265l1.922-21.532H16z"/><path fill="#ebebeb" d="M16 13.407h-4.09l-.282-3.165H16V7.151H8.25l.074.83l.759 8.517H16zm0 8.027l-.014.004l-3.442-.929l-.22-2.465H9.221l.433 4.852l6.332 1.758l.014-.004z"/><path fill="#fff" d="M15.989 13.407v3.091h3.806l-.358 4.009l-3.448.93v3.216l6.337-1.757l.046-.522l.726-8.137l.076-.83zm0-6.256v3.091h7.466l.062-.694l.141-1.567l.074-.83z"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">HTML</span>
            </div>  
            <div class="flex flex-col items-center">
                <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 128 128"><path fill="#0acf83" d="M45.5 129c11.9 0 21.5-9.6 21.5-21.5V86H45.5C33.6 86 24 95.6 24 107.5S33.6 129 45.5 129m0 0"/><path fill="#a259ff" d="M24 64.5C24 52.6 33.6 43 45.5 43H67v43H45.5C33.6 86 24 76.4 24 64.5m0 0"/><path fill="#f24e1e" d="M24 21.5C24 9.6 33.6 0 45.5 0H67v43H45.5C33.6 43 24 33.4 24 21.5m0 0"/><path fill="#ff7262" d="M67 0h21.5C100.4 0 110 9.6 110 21.5S100.4 43 88.5 43H67zm0 0"/><path fill="#1abcfe" d="M110 64.5c0 11.9-9.6 21.5-21.5 21.5S67 76.4 67 64.5S76.6 43 88.5 43S110 52.6 110 64.5m0 0"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">Figma</span>
            </div>
            <div class="flex flex-col items-center">
              <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 512 349"><path fill="#00758f" d="m152.31 230.297l15.56 50.487c3.496 11.463 4.954 19.465 4.37 24.026q12.765-34.188 17.839-74.513h18.71q-12.069 65.65-31.827 95.41c-10.262 15.289-21.504 22.933-33.746 22.933c-3.264 0-7.288-.986-12.063-2.944v-10.55c2.333.342 5.07.525 8.218.525q8.565-.002 13.816-4.742c4.193-3.849 6.292-8.175 6.292-12.97c0-3.274-1.637-9.993-4.896-20.157l-21.68-67.505zM33.223 199.266l28.5 86.956h.176l28.675-86.956h23.428c5.13 43.124 8.16 82.581 9.09 118.346H103.34q-1.044-50.148-5.768-94.32H97.4l-30.078 94.32H52.28l-29.896-94.32h-.176q-3.325 42.422-4.196 94.32H0c1.164-42.08 4.077-81.525 8.739-118.346z"/><path fill="#f29111" d="M352.498 197.51c30.657 0 45.986 19.586 45.986 58.739c0 21.276-4.61 37.347-13.821 48.204c-1.66 1.984-3.495 3.698-5.427 5.286l21.695 10.727l-.021-.001l-7.703 13.302l-28.253-16.485q-7.026 2.08-15.451 2.08c-15.053 0-26.297-4.387-33.731-13.15c-8.16-9.694-12.238-24.955-12.238-45.757c0-21.156 4.602-37.166 13.816-48.037c8.392-9.944 20.11-14.909 35.148-14.909m-93.88.172c10.957 0 20.92 2.932 29.894 8.775l-4.558 10.157c-7.679-3.264-15.25-4.903-22.716-4.903c-6.058 0-10.726 1.458-13.98 4.392c-3.272 2.908-5.296 6.65-5.296 11.212c0 7.01 4.994 13.089 14.215 18.225a816 816 0 0 1 9.031 5.011l.688.387l.345.194l.689.387l.344.194l.688.388c6.98 3.935 13.548 7.691 13.548 7.691c9.22 6.545 13.816 13.523 13.816 25.016c0 10.037-3.678 18.276-11.01 24.723c-7.337 6.418-17.194 9.636-29.538 9.636c-11.545 0-22.734-3.704-33.572-11.05l5.07-10.166c9.327 4.675 17.767 7.01 25.346 7.01c7.108 0 12.672-1.587 16.697-4.721c4.017-3.157 6.424-7.56 6.424-13.143c0-7.027-4.888-13.034-13.855-18.073a898 898 0 0 1-8.395-4.697l-.687-.389c-1.262-.713-2.533-1.435-3.778-2.142l-.675-.384c-6.055-3.444-11.29-6.453-11.29-6.453c-8.964-6.557-13.459-13.592-13.459-25.184c0-9.587 3.352-17.336 10.046-23.231q10.066-8.862 25.968-8.862m175.895 1.584v103.788h37.238v14.558h-56.124V199.266zm57.93 103.833v2.46h-4.094v12.04h-3.13v-12.04h-4.253v-2.46zm7.56 0l3.931 9.884l3.611-9.884h4.437v14.5h-2.95v-11.035l-4.11 11.035h-2.127l-4.117-11.035h-.158v11.035h-2.791v-14.5zM350.57 212.064c-18.066 0-27.104 14.91-27.104 44.71c0 17.07 2.395 29.448 7.176 37.163c4.428 7.14 11.363 10.703 20.806 10.703c18.066 0 27.103-15.026 27.103-45.064c0-16.831-2.395-29.103-7.17-36.822c-4.433-7.124-11.365-10.69-20.81-10.69"/><path fill="#00758f" d="M303.218 7.333c5.993-14.726 26.948-3.574 35.08 1.57c1.993 1.287 4.279 4.006 6.564 5.011c3.565.14 7.127.419 10.698.568c6.698 1.574 12.972 2.86 18.25 5.866c24.528 14.445 40.495 29.165 55.19 53.479c3.14 5.15 4.709 10.723 7.274 16.296c3.56 8.307 7.56 17.027 11.692 24.882c1.85 3.724 3.281 7.865 5.85 11.01c1.003 1.438 3.852 1.862 5.555 2.721c4.708 2.437 10.412 4.287 14.84 7.147c8.269 5.156 16.264 11.3 23.532 17.59c2.709 2.428 4.555 5.865 7.136 8.433v1.296c-2.291.703-4.574 1.423-6.859 2c-4.991 1.282-9.412.992-14.254 2.275c-2.992.868-6.707 2.013-9.845 2.304l.29.292c1.846 5.275 11.834 9.565 16.402 12.72c5.548 4.004 10.689 8.86 14.827 14.437c1.429 1.423 2.858 2.718 4.28 4.137c.994 1.438 1.274 3.298 2.28 4.58v.434c-1.114-.393-1.915-1.143-2.674-1.927l-.453-.473c-.453-.47-.91-.932-1.431-1.313c-3.148-2.15-6.274-4.722-9.422-6.721c-5.412-3.434-11.689-5.427-17.246-8.874c-3.142-2.001-6.137-4.28-9.132-6.57c-2.715-2.007-5.705-5.861-7.411-8.721c-1.005-1.58-1.143-3.437-2.291-4.58c.205-1.909 1.954-2.476 3.719-2.942l.406-.107c.609-.158 1.205-.316 1.725-.525c7.414-3.148 16.253-4.29 27.667-4.004c-.43-2.866-7.562-6.437-9.839-8.153c-4.57-3.294-9.409-6.731-14.257-9.729c-2.569-1.57-6.996-2.716-9.842-3.999c-3.851-1.574-12.41-3.147-14.544-6.145c-3.625-4.726-6.229-10.363-8.757-16.057l-.688-1.554l-.69-1.553c-2.988-6.857-6.7-14.006-9.695-21.027c-1.566-3.425-2.285-6.431-4-9.716c-10.407-20.158-25.81-37.035-44.485-48.904c-6.137-3.862-12.98-7.436-20.534-9.865c-4.281-1.293-9.419-.578-13.98-1.57h-3.002c-2.562-.722-4.701-3.438-6.7-4.87c-4.415-2.998-8.837-5.011-14.117-7.15c-1.85-.858-7.133-2.856-8.977-1.283c-1.142.287-1.721.718-2.002 1.864c-1.136 1.71-.137 4.286.57 5.863c2.142 4.57 5.134 7.286 7.85 11.148c2.416 3.425 5.417 7.287 7.13 11.011c3.696 8.005 5.417 16.874 8.842 24.878c1.27 3.01 3.279 6.435 5.128 9.15c1.567 2.155 4.416 3.713 5.278 6.441c1.718 2.86-2.572 12.297-3.565 15.294c-3.715 11.727-2.995 28.028 1.283 38.193l.228.536l.228.543c1.562 3.723 3.234 7.732 7.387 8.773c.286-.284 0-.135.567-.284c1.005-7.868 1.288-15.445 4-21.601c1.567-3.849 4.696-6.57 6.841-9.712c1.43.856 1.43 3.437 2.282 5.145c1.856 4.43 3.849 9.287 6.137 13.73c4.696 9.15 9.98 18.021 15.967 26.025c2.005 2.859 4.85 6.006 7.416 8.581c1.143.997 2.423 1.573 3.282 2.856h.28v.432c-4.278-1.577-6.99-6.003-10.402-8.587c-6.424-4.857-14.117-12.151-18.545-19.15c-1.852-4.018-3.854-7.869-5.85-11.867v-.289c-.853 1.142-.567 2.276-.994 4.004c-1.852 7.145-.426 15.296-6.843 17.866c-7.274 3.01-12.7-4.857-14.977-8.432c-7.276-11.866-9.269-31.884-4.138-48.043c1.14-3.577 1.295-7.867 3.285-10.723c-.43-2.582-2.42-3.288-3.571-4.87c-1.996-2.704-3.705-5.854-5.268-8.857c-3.002-5.866-5.138-12.875-7.417-19.166c-1.002-2.569-1.289-5.148-2.288-7.58c-1.704-3.712-4.845-7.436-7.268-10.72c-3.281-4.72-12.837-13.868-8.985-23.168m46.772 28.015c.381.382.841.716 1.317 1.045l.574.394c.765.53 1.506 1.088 1.96 1.848c.72 1.006.854 1.999 1.716 3.007c0 3.437-.996 5.722-3.007 7.146c0 0-.137.15-.278.29c-1.14-2.291-2.139-4.57-3.287-6.859c-1.414-1.998-3.413-3.583-4.565-5.866h-.277v-.287c1.721-.425 3.428-.718 5.847-.718"/></svg>
              <span class="text-md text-gray-700 dark:text-gray-300">MySql</span>
            </div>
            <!-- Ajoutez d'autres icônes de technologies ici -->
          </div>
        </div>
      </div>

      <!-- Boutons pour diriger vers le projet en ligne et le prochain projet -->
      <div class="flex justify-between">
        
        <NuxtLink to="/projects/sitePokemonPHP" class="bg-purple-700 hover:underline text-white py-2 px-4 rounded hover:bg-purple-600">
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
  "/img/screen_ap4.PNG",
  "/img/screen_ap3.PNG",
  "/img/screen_ap2.PNG",
  "/img/screen_ap1.PNG",
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
