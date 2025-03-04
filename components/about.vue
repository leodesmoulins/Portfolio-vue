<template>
    <div class="text-center py-16">
      <p class="text-xl text-gray-700 dark:text-gray-300">Présentation</p>
      <h1 class="text-4xl font-bold text-purple-700 dark:text-purple-300">A propos de moi</h1>
  
      <div class="mt-8 flex justify-center space-x-8">
        <div class="border border-purple-800 p-8 rounded-lg shadow-md bg-purple-200 dark:bg-gray-900 flex flex-col items-center w-40 h-40">
          <QuestionMarkCircleIcon class="h-6 w-6 text-purple-700 dark:text-purple-300"/>
          <p class="text-lg font-semibold text-purple-700 dark:text-purple-300 mt-4">Curieux</p>
        </div>
        <div class="border border-purple-800 p-8 rounded-lg shadow-md bg-purple-200 dark:bg-gray-900 flex flex-col items-center w-40 h-40">
          <Battery100Icon class="h-6 w-6 text-purple-700 dark:text-purple-300"/>
          <p class="text-lg font-semibold text-purple-700 dark:text-purple-300 mt-4">Autonome</p>
        </div>
        <div class="border border-purple-800 p-8 rounded-lg shadow-md bg-purple-200 dark:bg-gray-900 flex flex-col items-center w-40 h-40">
          <ChatBubbleLeftRightIcon class="h-6 w-6 text-purple-700 dark:text-purple-300"/>
          <p class="text-lg font-semibold text-purple-700 dark:text-purple-300 mt-4">Travail de groupe</p>
        </div>
    </div>
  
      <div class="mt-16 text-justify max-w-3xl mx-auto">
        <p class="mb-8 text-xl text-purple-700 dark:text-purple-300">
          A 19 ans, je suis actuellement en BTS SIO pour travailler dans le milieu du développement.
          Dans ma formation actuelle, j'ai pu acquérir les bases de plusieurs langages web (CSS, PHP, JS)
          ou bien différents frameworks (Ionic, Vue.js), la gestion de base de données telle que (PgAdmin, PhpMyAdmin).
        </p>
        <p class="mb-8 text-xl text-purple-700 dark:text-purple-300">
          J'ai pu ensuite exercer et améliorer ces connaissances avec un stage de 6 semaines en entreprise aux côtés d'un développeur fullstack expérimenté.
        </p>
        <p class="text-xl text-purple-700 dark:text-purple-300">
          J'aimerais maintenant continuer mes études avec un Bachelor CDA en alternance à la CESI du Mans.
        </p>
      </div>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { QuestionMarkCircleIcon, ChatBubbleLeftRightIcon } from '@heroicons/vue/24/outline'
  import { Battery100Icon } from '@heroicons/vue/24/solid'
  </script>
  
  <style scoped>
  </style>