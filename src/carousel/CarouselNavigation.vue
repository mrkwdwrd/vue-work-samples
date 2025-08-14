<script setup>
const props = defineProps({
  count: {
    type: Number,
    required: true
  },
  current: {
    type: Number,
    required: true
  }
})
const emits = defineEmits(['show'])

</script>
<template>
  <nav class="fixed block bottom-2 bg-gray-800 px-4 py-3 rounded-full">
    <ul class="flex gap-2">
      <li
        v-for="(n, i) in props.count"
        :key="i">
        <button
          class="block rounded-full bg-gray-400 p-1 cursor-pointer"
          :class="[{'bg-white': current === i}]"
          @click="emits('show', i)"
        />
      </li>
    </ul>
  </nav>
</template>
