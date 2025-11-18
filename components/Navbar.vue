<script setup lang="ts">
import type { NavigationMenuItem } from '@nuxt/ui'

const route = useRoute()

// Menu items com âncoras para as seções
const items = computed<NavigationMenuItem[]>(() => [
  {
    label: 'Como funciona',
    to: '/#como-funciona',
    active: route.hash === '#como-funciona'
  },
  {
    label: 'Integrações',
    to: '/#integracoes',
    active: route.hash === '#integracoes'
  },
  {
    label: 'Por quê Kivo IA',
    to: '/#por-que-ia',
    active: route.hash === '#por-que-ia'
  }
])
</script>

<template>
  <UHeader
    title="Kivo IA"
    to="/"
    class="!bg-transparent !backdrop-blur-xl !fixed !top-0 !left-0 !right-0 !z-50"
  >
    <template #title>
      <span class="text-xl font-bold text-highlighted">Kivo IA</span>
    </template>

    <UNavigationMenu
      :items="items"
      variant="link"
      class="hidden lg:flex"
    />

    <template #right>
      <UButton
        to="/#agendar"
        color="primary"
        variant="solid"
        size="sm"
        class="hidden lg:inline-flex"
      >
        Agendar reunião
      </UButton>
    </template>

    <!-- Mobile menu -->
    <template #body>
      <UNavigationMenu
        :items="items"
        orientation="vertical"
        class="lg:hidden"
      />

      <div class="mt-4 lg:hidden">
        <UButton
          to="/#agendar"
          color="primary"
          variant="solid"
          size="md"
          block
        >
          Agendar reunião
        </UButton>
      </div>
    </template>
  </UHeader>
</template>
