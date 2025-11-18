<script setup lang="ts">
import { section4 } from '~/content/copy'
</script>

<template>
  <UPageSection id="como-funciona" class="bg-[#161616]">
    <UContainer>
      <h2 class="text-3xl sm:text-4xl lg:text-5xl tracking-tight font-bold text-highlighted text-pretty text-center leading-[48px]">{{ section4.title }}</h2>
      <p class="mt-6 text-base sm:text-lg text-muted text-pretty text-center max-w-3xl mx-auto font-normal">{{ section4.subtitle }}</p>
    </UContainer>

    <div class="mt-0 max-w-4xl mx-auto">
      <div class="space-y-4">
        <UCard
          v-for="(item, i) in section4.items"
          :key="i"
          variant="subtle"
          class="group hover:ring-primary/50 transition-all duration-300"
        >
          <div class="flex items-start gap-4">
            <div class="flex-shrink-0">
              <div class="w-10 h-10 rounded-full bg-primary/10 flex items-center justify-center text-primary font-semibold group-hover:bg-primary/20 transition-colors duration-300">
                {{ i + 1 }}
              </div>
            </div>
            <div class="flex-1 pt-1.5">
              <p class="text-base sm:text-lg text-default font-medium leading-relaxed">{{ item }}</p>
            </div>
          </div>
        </UCard>
      </div>
    </div>
  </UPageSection>
</template>
