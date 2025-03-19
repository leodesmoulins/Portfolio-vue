<template>
  <div class="w-full bg-purple-100 dark:bg-gray-900 shadow-md fixed top-0 left-0 z-50">
    <nav class="container mx-auto py-4 px-6 flex justify-between items-center">
      <!-- Prénom à gauche -->
      <NuxtLink to="/" class="text-purple-700 dark:text-purple-300 font-bold text-xl">Léo</NuxtLink>

      <!-- Icône à droite -->
      <div @click="$emit('toggleMode')" class="cursor-pointer">
        <MoonIcon v-if="isDarkMode" class="h-6 w-6 text-purple-700 dark:text-purple-300" />
        <SunIcon v-else class="h-6 w-6 text-purple-700 dark:text-purple-300" />
      </div>
    </nav>
  </div>
</template>

<script lang="ts" setup>
import { defineProps } from 'vue'
import { SunIcon, MoonIcon } from '@heroicons/vue/24/outline'

const props = defineProps({
  isDarkMode: Boolean
})
</script>
