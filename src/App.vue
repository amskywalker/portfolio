<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="flex justify-between items-center w-full px-60 py-12 text-white font-bold">
    <div class="flex flex-row items-center justify-between w-full">
      <!-- Menu principal -->
      <nav class="flex items-center gap-6">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">Sobre</RouterLink>
        <RouterLink to="/project">Projetos</RouterLink>
      </nav>

      <nav class="flex items-center gap-6">
        <a href="https://instagram.com" target="_blank" class="text-purple-700">Linkedin</a>
        <a href="https://github.com" target="_blank" class="text-purple-700">GitHub</a>
        <a href="https://github.com" target="_blank" class="text-purple-700">Email</a>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
</style>