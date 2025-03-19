<template>
  <div class="text-center py-16">
    <p class="text-xl text-gray-800 dark:text-gray-300">Présentation</p>
    <h1 class="text-4xl font-bold text-purple-800 dark:text-purple-400">À propos de moi</h1>

    <!-- Cartes des compétences -->
    <div class="mt-8 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 justify-items-center">
      <div class="border border-purple-800 p-6 rounded-lg shadow-md bg-purple-200 dark:bg-gray-800 flex flex-col items-center w-40 h-40">
        <QuestionMarkCircleIcon class="h-8 w-8 text-purple-800 dark:text-purple-400" />
        <p class="text-lg font-semibold text-purple-900 dark:text-purple-400 mt-4">Curieux</p>
      </div>
      <div class="border border-purple-800 p-6 rounded-lg shadow-md bg-purple-200 dark:bg-gray-800 flex flex-col items-center w-40 h-40">
        <Battery100Icon class="h-8 w-8 text-purple-800 dark:text-purple-400" />
        <p class="text-lg font-semibold text-purple-900 dark:text-purple-400 mt-4">Autonome</p>
      </div>
      <div class="border border-purple-800 p-6 rounded-lg shadow-md bg-purple-200 dark:bg-gray-800 flex flex-col items-center w-40 h-40">
        <ChatBubbleLeftRightIcon class="h-8 w-8 text-purple-800 dark:text-purple-400" />
        <p class="text-lg font-semibold text-purple-900 dark:text-purple-400 mt-4">Travail de groupe</p>
      </div>
    </div>

    <!-- Texte de présentation -->
    <div class="mt-16 max-w-3xl mx-auto px-4">
      <p class="mb-8 text-lg text-gray-900 dark:text-gray-300 text-center sm:text-left">
        À 19 ans, je suis actuellement en BTS SIO pour travailler dans le milieu du développement.
        Dans ma formation actuelle, j'ai pu acquérir les bases de plusieurs langages web (CSS, PHP, JS)
        ainsi que des frameworks comme Ionic et Vue.js. J’ai également appris à gérer des bases de données
        avec PgAdmin et PhpMyAdmin.
      </p>
      <p class="mb-8 text-lg text-gray-900 dark:text-gray-300 text-center sm:text-left">
        J’ai pu ensuite exercer et améliorer ces connaissances grâce à un stage de 6 semaines en entreprise
        aux côtés d’un développeur fullstack expérimenté.
      </p>
      <p class="text-lg text-gray-900 dark:text-gray-300 text-center sm:text-left">
        J’aimerais maintenant continuer mes études avec un Bachelor CDA en alternance à la CESI du Mans.
      </p>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { QuestionMarkCircleIcon, ChatBubbleLeftRightIcon } from '@heroicons/vue/24/outline'
import { Battery100Icon } from '@heroicons/vue/24/solid'
</script>
