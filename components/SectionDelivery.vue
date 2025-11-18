<script setup lang="ts">
import { section8 } from '~/content/copy'
</script>

<template>
  <UPageSection :title="section8.title" class="bg-default !pt-0 -mt-64 relative">
    <!-- Glow central -->
    <div class="absolute inset-0 flex items-center justify-center pointer-events-none">
      <div class="w-[600px] h-[600px] relative">
        <div
          class="absolute inset-0 blur-3xl"
          style="background: radial-gradient(circle at center, rgba(154, 230, 0, 0.4) 0%, rgba(154, 230, 0, 0.2) 30%, rgba(154, 230, 0, 0.1) 50%, transparent 70%)"
        />
        <div
          class="absolute inset-0 blur-xl"
          style="background: radial-gradient(circle at center, rgba(154, 230, 0, 0.3) 0%, rgba(154, 230, 0, 0.15) 40%, transparent 60%)"
        />
      </div>
    </div>

    <div class="mt-8 relative z-10">
      <UPageList>
        <ul class="space-y-3">
          <li v-for="(item, i) in section8.items" :key="i" class="text-default">{{ item }}</li>
        </ul>
      </UPageList>
    </div>
  </UPageSection>
</template>
