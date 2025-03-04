<template>
  <div class="w-full bg-purple-100 dark:bg-gray-900 shadow-md fixed z-100">
    <nav class="container mx-auto py-4 px-64 m-2 flex justify-between items-center">
      <ul class="flex items-center space-x-4">
        <li><NuxtLink to="/" class="text-purple-700 dark:text-purple-300 font-bold text-xl">Léo</NuxtLink></li>
      </ul>
      <ul class="flex items-center space-x-3">
        <li @click="$emit('toggleMode')" class="cursor-pointer">
          <MoonIcon v-if="isDarkMode" class="h-6 w-6 text-purple-700 dark:text-purple-300" />
          <SunIcon v-else class="h-6 w-6 text-purple-700 dark:text-purple-300" />
        </li>
      </ul>
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