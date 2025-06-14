<script setup lang="ts">
import TemplateCard from '@/components/TemplateCard.vue'

import templates from '@/assets/common.json'

const store = useStore()
const currentYear = new Date().getFullYear()
</script>

<template>
  <main class="max-w-screen-xl mx-auto p-6">
    <div class="columns-1 md:columns-3 gap-4">
      <div v-for="(item, index) in templates" :key="index" class="mb-4 break-inside-avoid">
        <TemplateCard :title="item.title" :content="item.content" />
      </div>
    </div>
  </main>
  <footer>
    <p>text</p>
  </footer>
</template>
