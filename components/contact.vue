<template>
  <div class="text-center py-16">
    <p class="text-xl text-gray-700 dark:text-gray-300">Get in touch</p>
    <h1 class="text-4xl font-bold text-purple-700 dark:text-purple-300">
      Contactez Moi
    </h1>
    <div class="min-h-screen py-6 flex flex-col justify-center sm:py-12">
      <div class="relative py-3 sm:max-w-4xl sm:mx-auto">
        <div
          class="absolute inset-0 bg-gradient-to-r from-purple-700 to-purple-300 dark:from-purple-300 dark:to-purple-700 shadow-lg transform -skew-y-6 sm:skew-y-0 sm:-rotate-6 sm:rounded-3xl"
        ></div>
        <div
          class="relative px-6 py-10 bg-purple-500 shadow-lg sm:rounded-3xl sm:p-12 text-white"
        >
          <div class="text-center pb-6">
            <h1 class="text-3xl">Un petit message pour en savoir plus ?</h1>
          </div>

          <div class="flex flex-col sm:flex-row justify-between gap-8">
            <!-- Formulaire -->
            <form class="w-full sm:w-1/2 max-w-lg mx-auto" action="https://formspree.io/f/xgvogrvg" method="POST">
              <input
                class="shadow mb-4 border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-purple-400"
                type="text"
                placeholder="Nom"
                name="name"
                required
              />

              <input
                class="shadow mb-4 border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-purple-400"
                type="email"
                placeholder="Email"
                name="email"
                required
              />

              <input
                class="shadow mb-4 border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-purple-400"
                type="text"
                placeholder="Sujet"
                name="_subject"
                required
              />

              <textarea
                class="shadow mb-4 border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:ring-2 focus:ring-purple-400 resize-none"
                placeholder="Tapez votre message ici..."
                name="message"
                required
                rows="5"
              ></textarea>

              <div class="flex justify-center">
                <input
                  class="shadow bg-purple-700 hover:bg-purple-600 text-white font-bold py-2 px-4 rounded focus:outline-none focus:ring-2 focus:ring-purple-400 cursor-pointer"
                  type="submit"
                  value="Envoyer ➤"
                />
              </div>
            </form>

            <!-- Éléments supplémentaires -->
            <div class="w-full sm:w-1/2 text-center sm:text-left">
              <h2 class="text-2xl font-bold mb-4">Informations de contact</h2>
              <p class="mb-4 text-lg">Vous pouvez également me contacter via :</p>
              <ul class="text-lg space-y-2">
                <li>Email: leo.desmoulins@gmail.com</li>
                <li>Téléphone: 07 50 63 60 74</li>
              </ul>
              <h2 class="text-2xl font-bold mt-8 mb-4">Suivez-moi</h2>
              <div class="flex justify-center sm:justify-start space-x-4">
                <a href="#" class="hover:underline text-xl">LinkedIn</a>
                <a href="#" class="hover:underline text-xl">GitHub</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
