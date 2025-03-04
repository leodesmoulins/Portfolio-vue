<template>
  <div class="text-center py-16">
    <p class="text-lg text-gray-700 dark:text-gray-300">Hello, je suis</p>
    <h1 class="text-4xl font-bold text-purple-700 dark:text-purple-300">
      Léo Desmoulins
    </h1>
    <p class="text-lg text-gray-700 dark:text-gray-300">Développeur</p>

    <div class="mt-8 space-x-8">
      <button
        class="px-8 py-4 bg-purple-700 text-white rounded-lg hover:bg-purple-800"
      >
        <a href="https://www.linkedin.com/in/léo-desmoulins-056039280/" target="_blank">
          <div class="flex items-center justify-center space-x-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 128 128"
            >
              <path
                fill="#0076b2"
                d="M116 3H12a8.91 8.91 0 0 0-9 8.8v104.42a8.91 8.91 0 0 0 9 8.78h104a8.93 8.93 0 0 0 9-8.81V11.77A8.93 8.93 0 0 0 116 3"
              />
              <path
                fill="#fff"
                d="M21.06 48.73h18.11V107H21.06zm9.06-29a10.5 10.5 0 1 1-10.5 10.49a10.5 10.5 0 0 1 10.5-10.49m20.41 29h17.36v8h.24c2.42-4.58 8.32-9.41 17.13-9.41C103.6 47.28 107 59.35 107 75v32H88.89V78.65c0-6.75-.12-15.44-9.41-15.44s-10.87 7.36-10.87 15V107H50.53z"
              />
            </svg>
            <p>Linkedin</p>
          </div>
        </a>
      </button>
      <button
        @click="handleDownload"
        class="px-8 py-4 bg-purple-700 text-white rounded-lg hover:bg-purple-800"
      >
        <div class="flex items-center justify-center space-x-2">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
          >
            <path
              fill="currentColor"
              d="m12 16l-5-5l1.4-1.45l2.6 2.6V4h2v8.15l2.6-2.6L17 11zm-6 4q-.825 0-1.412-.587T4 18v-3h2v3h12v-3h2v3q0 .825-.587 1.413T18 20z"
            />
          </svg>
          <p>Télécharger mon CV</p>
        </div>
      </button>
      <button
        @click="scrollToSection('#about')"
        class="px-8 py-4 bg-purple-700 text-white rounded-lg hover:bg-purple-800"
      >
        <div class="flex items_center justify-center spaxe-x-2">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
          >
            <path
              fill="currentColor"
              d="M12 12q-1.65 0-2.825-1.175T8 8t1.175-2.825T12 4t2.825 1.175T16 8t-1.175 2.825T12 12m-8 8v-2.8q0-.85.438-1.562T5.6 14.55q1.55-.775 3.15-1.162T12 13t3.25.388t3.15 1.162q.725.375 1.163 1.088T20 17.2V20z"
            />
          </svg>
          <p>A propos de moi</p>
        </div>
      </button>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollToPlugin } from "gsap/ScrollToPlugin";

gsap.registerPlugin(ScrollToPlugin);

const cvPath = ref("/CV Léo Desmoulins.pdf");

onMounted(() => {
  // Vérifie si le fichier existe à cet emplacement
  const testImage = new Image();
  testImage.onload = () => {
    console.log("Le fichier existe");
  };
  testImage.onerror = () => {
    console.error("Le fichier n'existe pas à cet emplacement");
  };
});

const handleDownload = () => {
  const link = document.createElement("a");
  link.href = cvPath.value;
  link.setAttribute("download", "CV Léo Desmoulins.pdf");
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
};

const scrollToSection = (id: string) => {
  gsap.to(window, { duration: 1, scrollTo: id });
};
</script>

<style scoped></style>
