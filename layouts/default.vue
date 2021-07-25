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

.field-item {
  @apply mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50;
}
</style>