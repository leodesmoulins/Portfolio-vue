<template>
  <div class="text-center py-16">
    <h1 class="text-4xl font-bold text-purple-700 dark:text-purple-300">
      Mes Projets
    </h1>

    <div class="mt-8 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 justify-items-center">
      <div
        v-for="project in projects"
        :key="project.title"
        class="border border-purple-800 p-6 rounded-lg shadow-md bg-purple-100 dark:bg-gray-900 flex flex-col items-center w-full max-w-[320px] h-auto transition-transform transform hover:scale-105"
      >
        <div class="border border-purple-800 rounded-lg shadow-md bg-purple-100 dark:bg-gray-800 w-full h-48 flex items-center justify-center mb-3 overflow-hidden">
          <img :src="project.image" :alt="project.title" class="rounded-lg object-cover w-full h-full">
        </div>
        <p class="text-2xl font-bold text-purple-700 dark:text-purple-300">{{ project.title }}</p>
        <NuxtLink :to="project.link" class="mt-4 text-purple-700 dark:text-purple-300 hover:underline">Voir le projet</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const projects = [
  { title: "AcbClean", image: "/img/img_acbclean.png", link: "/projects/siteAcbClean" },
  { title: "Ancien Portfolio", image: "/img/img_oldPortfolio.PNG", link: "/projects/oldPortfolio" },
  { title: "Application Weclimb", image: "/img/img_weclimb.PNG", link: "/projects/appWeclimb" },
  { title: "CodePlayground", image: "/img/img_codeplayground.PNG", link: "/projects/siteCodePlayground" },
  { title: "Hijobs", image: "/img/img_hiJobs.PNG", link: "/projects/siteHijobs" },
  { title: "Projet PHP", image: "/img/img_pokemonPhp.PNG", link: "/projects/sitePokemonPHP" },
  { title: "Site Webflow", image: "/img/img_webflow.png", link: "/projects/siteWebFlow" }
];
</script>
