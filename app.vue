<script setup lang="ts">
// Force dark mode imediatamente para prevenir FOUC
useHead({
  htmlAttrs: {
    class: 'dark',
    style: 'color-scheme: dark; background-color: #000000;'
  },
  bodyAttrs: {
    class: 'antialiased scheme-dark',
    style: 'background-color: #000000; color: #ffffff;'
  }
})
</script>

<template>
  <UApp>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
    <NuxtRouteAnnouncer />
  </UApp>
</template>
