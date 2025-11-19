<script setup lang="ts">
import { hero } from '~/content/copy'
import CustomCTAButton from '~/components/CustomCTAButton.vue'

const dashboardImage = 'https://ckwjxuxatlqnuxbfltul.supabase.co/storage/v1/object/sign/docs-kivo-ai/img-dashboard.png?token=eyJraWQiOiJzdG9yYWdlLXVybC1zaWduaW5nLWtleV8wZmZiNWI3ZC0wNWJkLTQxNTQtYTFlZS1kM2Y5MWFhMjc4ZDIiLCJhbGciOiJIUzI1NiJ9.eyJ1cmwiOiJkb2NzLWtpdm8tYWkvaW1nLWRhc2hib2FyZC5wbmciLCJpYXQiOjE3NjM0ODc3MzUsImV4cCI6MjExMDM4MzczNX0.wt5MNiq5Q1rI7NxuxI4o9VpRUJjW8sYUlVVWQwKiwYU'
const dashboardImageMobile = 'https://ckwjxuxatlqnuxbfltul.supabase.co/storage/v1/object/sign/docs-kivo-ai/img-dashboard-mobile.png?token=eyJraWQiOiJzdG9yYWdlLXVybC1zaWduaW5nLWtleV8wZmZiNWI3ZC0wNWJkLTQxNTQtYTFlZS1kM2Y5MWFhMjc4ZDIiLCJhbGciOiJIUzI1NiJ9.eyJ1cmwiOiJkb2NzLWtpdm8tYWkvaW1nLWRhc2hib2FyZC1tb2JpbGUucG5nIiwiaWF0IjoxNzYzNTA1MzY5LCJleHAiOjIxMTA0MDEzNjl9.JbKImCpAkIEvK0FcKx6JoqR8nwPDdSrNRDlk_FdVCrw'
</script>

<template>
  <div class="relative min-h-screen">
    <!-- Background animado -->
    <HeroBackground />

    <!-- Conteúdo da hero section -->
    <UPageHero
      id="hero"
      class="relative z-10"
    >
      <template #title>
        <h1 class="hero-title-enter text-5xl sm:text-6xl lg:text-7xl font-bold tracking-tight">
          {{ hero.title }}
        </h1>
      </template>

      <template #description>
        <p class="hero-description-enter text-lg sm:text-xl text-gray-400 max-w-3xl mx-auto">
          {{ hero.subtitle }}
        </p>
      </template>

      <template #links>
        <div class="hero-cta-enter flex flex-wrap gap-x-6 gap-y-3 justify-center">
          <CustomCTAButton to="#agendar" size="xl">
            {{ hero.cta }}
          </CustomCTAButton>
          <UButton
            to="#apresentacao"
            size="xl"
            color="neutral"
            variant="outline"
          >
            Como funciona
          </UButton>
        </div>
      </template>

      <!-- Container com imagem do dashboard - Mobile -->
      <div class="hero-image-enter relative border border-[#27272A] rounded-lg overflow-hidden mt-0 block md:hidden">
        <img
          :src="dashboardImageMobile"
          alt="Dashboard Kivo IA Mobile"
          class="w-full h-auto grayscale"
        >
        <!-- Sombra gradient na parte inferior -->
        <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-[#000000] to-transparent pointer-events-none"/>
      </div>

      <!-- Container com imagem do dashboard - Desktop -->
      <div class="hero-image-enter relative border border-[#27272A] rounded-lg overflow-hidden mt-0 hidden md:block">
        <img
          :src="dashboardImage"
          alt="Dashboard Kivo IA"
          class="w-full h-auto grayscale"
        >
        <!-- Sombra gradient na parte inferior -->
        <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-[#000000] to-transparent pointer-events-none"/>
      </div>
    </UPageHero>
  </div>
</template>
