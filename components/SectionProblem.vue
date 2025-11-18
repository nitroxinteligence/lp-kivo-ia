<script setup lang="ts">
import { section2 } from '~/content/copy'
</script>

<template>
  <UPageSection class="bg-default">
    <UContainer>
      <h2 class="text-3xl sm:text-4xl lg:text-5xl tracking-tight font-bold text-highlighted text-pretty text-center leading-tight">{{ section2.title }}</h2>
      <p class="mt-6 text-base sm:text-lg text-muted text-pretty text-center max-w-3xl mx-auto font-normal">{{ section2.subtitle }}</p>
    </UContainer>
  </UPageSection>
</template>
