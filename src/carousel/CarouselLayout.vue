<script setup>
import { onMounted, ref } from 'vue'
import CarouselSlide from './CarouselSlide.vue'

const props = defineProps({
  slideComponents: {
    type: Array,
    required: true
  }
})

const show = ref(0)

const keyListener = event => {
  if (event.key === 'ArrowRight') {
    handleNext()
  }
  if (event.key === 'ArrowLeft') {
    handlePrevious()
  }
}

const handlePrevious = () => {
  show.value--
}
const handleNext = () => {
  show.value++
}

onMounted(() => {
  document.addEventListener('keydown', keyListener)
})
</script>

<template>
  <CarouselSlide
    v-for="(cmp, i) in props.slideComponents"
    :key="i"
    :show="show === i">
    <component :is="cmp" />
  </CarouselSlide>
</template>
