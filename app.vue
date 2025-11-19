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
  },
  link: [
    {
      rel: 'icon',
      type: 'image/png',
      href: 'https://ckwjxuxatlqnuxbfltul.supabase.co/storage/v1/object/sign/docs-kivo-ai/Logo%20-%20Kivo%20IA.png?token=eyJraWQiOiJzdG9yYWdlLXVybC1zaWduaW5nLWtleV8wZmZiNWI3ZC0wNWJkLTQxNTQtYTFlZS1kM2Y5MWFhMjc4ZDIiLCJhbGciOiJIUzI1NiJ9.eyJ1cmwiOiJkb2NzLWtpdm8tYWkvTG9nbyAtIEtpdm8gSUEucG5nIiwiaWF0IjoxNzYzNTE4Nzk1LCJleHAiOjIxMTA0MTQ3OTV9.XGWH8hEQaCkvzeGc_yKc5DngDMgKfE1zocfhCURDANc'
    },
    {
      rel: 'apple-touch-icon',
      href: 'https://ckwjxuxatlqnuxbfltul.supabase.co/storage/v1/object/sign/docs-kivo-ai/Logo%20-%20Kivo%20IA.png?token=eyJraWQiOiJzdG9yYWdlLXVybC1zaWduaW5nLWtleV8wZmZiNWI3ZC0wNWJkLTQxNTQtYTFlZS1kM2Y5MWFhMjc4ZDIiLCJhbGciOiJIUzI1NiJ9.eyJ1cmwiOiJkb2NzLWtpdm8tYWkvTG9nbyAtIEtpdm8gSUEucG5nIiwiaWF0IjoxNzYzNTE4Nzk1LCJleHAiOjIxMTA0MTQ3OTV9.XGWH8hEQaCkvzeGc_yKc5DngDMgKfE1zocfhCURDANc'
    }
  ]
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
