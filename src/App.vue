<script setup>
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const shouldFixNav = () => {
  return route.path === '/'
}
const showNav = ref(shouldFixNav())

const navActive = () => {
  showNav.value = true
}
const navInactive = () => {
  setTimeout(() => {
    showNav.value = shouldFixNav() || false
  }, 500)
}

onMounted(() => {
  showNav.value = shouldFixNav()
})
</script>

<template>
  <header
    :class="['text-white', {showNav}]"
    @mouseenter="navActive"
    @mouseleave="navInactive">
    <nav class="flex gap-8 bg-gray-800">
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

<style lang="scss" scoped>
  header {
    padding: 10px 20px;
    position: fixed;
    z-index: 2;
    width: 100%;
    nav {
      position: absolute;
      width: 100%;
      height: auto;
      top: -100px;
      left: 0;
      right: 0;
      padding: 10px 20px;
      transition: all 0.5s ease-in-out;
    }
    &.showNav,
    &:hover {
      nav {
        top: 0;
      }
    }
  }

  .viewport {
    position: fixed;
    top: 0;
    bottom: 0;
    width: 100%;
  }
</style>
