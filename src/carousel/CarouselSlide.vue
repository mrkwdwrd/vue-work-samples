<script setup>
import { onMounted } from 'vue'

const props = defineProps({
  show: Boolean
})

const emits = defineEmits(['load'])

onMounted(() => {
  emits('load')
})
</script>

<template>
  <transition name="slide-fade">
    <section
      v-if="props.show"
      class="w-full h-full fixed flex justify-center items-center">
      <slot />
    </section>
  </transition>
</template>

<style scoped>
.slide-fade-enter-active {
  transition: all 0.5s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.5s ease-out;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
</style>
