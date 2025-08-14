<script setup></script>

<template>
  <header class="bg-gray-800 text-white">
    <nav class="flex gap-8">
      <RouterLink :to="{ name: 'Home' }">
        Home
      </RouterLink>
      <RouterLink :to="{ name: 'Carousel' }">
        Carousel
      </RouterLink>
    </nav>
  </header>
  <div class="viewport">
    <RouterView />
  </div>
</template>

<style scoped>
  header {
    padding: 10px 20px;
    position: fixed;
    z-index: 2;
    width: 100%;
  }
  .viewport {
    position: fixed;
    top: 0;
    bottom: 0;
    width: 100%;
  }
</style>
