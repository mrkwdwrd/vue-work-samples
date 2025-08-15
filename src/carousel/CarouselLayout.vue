<script setup>
import { nextTick, onBeforeUnmount, onMounted, ref } from 'vue'
import CarouselSlide from './CarouselSlide.vue'
import CarouselNavigation from './CarouselNavigation.vue'

const props = defineProps({
  slideComponents: {
    type: Array,
    required: true
  }
})

const current = ref(0)
const min = 0
const max = props.slideComponents.length - 1
const showNav = ref(false)

const keyListener = event => {
  if (event.key === 'ArrowRight') {
    handleNext()
  }
  if (event.key === 'ArrowLeft') {
    handlePrevious()
  }
}

const handlePrevious = () => {
  if (current.value > min) {
    current.value--
  }
}
const handleNext = () => {
  if (current.value < max) {
    current.value++
  }
}

onMounted(() => {
  document.addEventListener('keydown', keyListener)
  nextTick(() => {
    showNav.value = max > 1
  })
})

onBeforeUnmount(() => {
  document.removeEventListener('keydown', keyListener)
})
</script>

<template>
  <CarouselSlide
    v-for="(cmp, i) in props.slideComponents"
    :key="i"
    :show="current === i">
    <component :is="cmp" />
  </CarouselSlide>

  <transition name="slide-up">
    <CarouselNavigation
      v-if="showNav"
      :count="props.slideComponents.length"
      :current="current"
      @show="val => { current = val }"
    />
  </transition>
</template>

<style scoped>
  .slide-up-enter-active {
    transition: all 0.5s cubic-bezier(0.3, 0.2, 0.2, 1.4);
  }

  .slide-up-enter-from {
    transform: translateY(100%);
  }
</style>
