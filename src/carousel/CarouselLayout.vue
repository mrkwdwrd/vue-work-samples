<script setup>
import { onMounted, ref } from 'vue'
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
})
</script>

<template>
  <CarouselSlide
    v-for="(cmp, i) in props.slideComponents"
    :key="i"
    :show="current === i">
    <component :is="cmp" />
  </CarouselSlide>
  <CarouselNavigation
    :count="props.slideComponents.length"
    :current="current"
  />
</template>
