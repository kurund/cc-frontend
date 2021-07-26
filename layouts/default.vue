<template>
  <div class="bg-white">
    <Navbar />
    <Nuxt />
  </div>
</template>

<style>
.blue-button {
  @apply bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded;
}

.green-button {
  @apply bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded;
}

.purple-button {
  @apply inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500;
}

.input-field {
  @apply mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md;
}

.radio-field {
  @apply focus:ring-indigo-500 h-4 w-4 text-indigo-600 border-gray-300 ml-3;
}

.select-field {
  @apply mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm;
}
</style>