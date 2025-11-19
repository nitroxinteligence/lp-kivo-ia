<script setup lang="ts">
import { section9 } from '~/content/copy'
import CustomCTAButton from '~/components/CustomCTAButton.vue'
</script>

<template>
  <div class="py-16 sm:py-24 lg:py-32 bg-default">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="border border-[#27272A] rounded-[20px] overflow-hidden">
        <UPageSection
          id="agendar"
          :title="section9.title"
          :ui="{
            title: 'text-3xl sm:text-4xl md:text-5xl lg:text-6xl text-pretty tracking-tight font-bold text-highlighted'
          }"
        >
          <template #links>
            <div class="flex flex-wrap gap-x-6 gap-y-3 justify-center">
              <CustomCTAButton
                to="https://wa.me/5511991943683?text=Ol%C3%A1!%20Vim%20pelo%20site%20da%20KIVO%20IA%20e%20gostaria%20de%20mais%20informa%C3%A7%C3%B5es"
                size="lg"
                external
                target="_blank"
              >
                {{ section9.cta }}
              </CustomCTAButton>
            </div>
          </template>
        </UPageSection>
      </div>
    </div>
  </div>
</template>
