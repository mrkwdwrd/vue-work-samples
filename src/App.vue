<script setup></script>

<template>
  <header>
    <nav>
      <RouterLink :to="{ name: 'Home' }">
        Home
      </RouterLink>
    </nav>
  </header>
  <main>
    <RouterView />
  </main>
</template>

<style scoped></style>
