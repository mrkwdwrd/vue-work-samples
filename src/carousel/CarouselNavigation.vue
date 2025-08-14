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
</script>
<template>
  <nav class="fixed block bottom-0 bg-gray-800 px-4 pb-3 pt-4 rounded-t-xl">
    <ul class="flex gap-2">
      <li
        v-for="(n, i) in props.count"
        :key="i">
        <button
          class="block rounded-full bg-gray-400 p-1"
          :class="[{'bg-white': current === i}]"
        />
      </li>
    </ul>
  </nav>
</template>
