<script setup>
import CarouselLayout from '@/carousel/CarouselLayout.vue'
import SlideOne from '@/slides/SlideOne.vue'
import SlideThree from '@/slides/SlideThree.vue'
import SlideTwo from '@/slides/SlideTwo.vue'

const slides = [
  SlideOne,
  SlideTwo,
  SlideThree
]
</script>

<template>
  <main class="h-full w-full flex justify-center items-center">
    <CarouselLayout :slide-components="slides" />
  </main>
</template>
