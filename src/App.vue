<script setup></script>

<template>
  <header>
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
    background: rgba(0, 0, 0, 0.5);
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
