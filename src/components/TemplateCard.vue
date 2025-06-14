<script setup lang="ts">
import { ref } from 'vue'

// Объявляем props
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  content: {
    type: String,
    required: true,
  },
})

// Стейт для анимации
const copied = ref(false)

function copyContent() {
  navigator.clipboard
    .writeText(props.content)
    .then(() => {
      copied.value = true
      // Через 2 секунды возвращаем обратно
      setTimeout(() => {
        copied.value = false
      }, 2000)
    })
    .catch(err => {
      console.error('Ошибка копирования:', err)
    })
}
</script>

<template>
  <div
    class="template bg-sky-50 flex flex-col justify-start items-start transition-colors duration-300 ease-out hover:bg-slate-200"
  >
    <div class="flex justify-between items-center w-full mb-2">
      <h3 class="m-0 font-bold">{{ title }}</h3>
      <button
        @click="copyContent"
        class="px-2 py-1 bg-slate-300 border border-gray-300 rounded-md text-sm transition-all duration-300 ease-out hover:bg-white"
      >
        <span v-if="!copied">[Copy]</span>
        <span v-else class="text-green-600 transition-opacity duration-300">Copied!</span>
      </button>
    </div>
    <span style="white-space: pre-wrap">{{ content }}</span>
  </div>
</template>

<style scoped>
.template {
  background-image: var(--bg-noise);
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  max-width: 400px;
}

h3 {
  margin-top: 0;
}
</style>
