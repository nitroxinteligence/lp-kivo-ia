<script setup lang="ts">
const textParts = [
  'Automação Inteligente',
  'IA para Proteção Veicular',
  'Atendimento 24/7',
  'Gestão Simplificada'
]

const repeatedParts = computed(() => {
  const parts = [...textParts, ...textParts, ...textParts, ...textParts]
  return parts
})
</script>

<template>
  <section class="bg-[#161616] py-16 sm:py-24">
    <div class="w-full overflow-hidden whitespace-nowrap">
      <div class="inline-block text-4xl sm:text-5xl lg:text-6xl font-bold text-highlighted/20 animate-scroll">
        <template v-for="(part, index) in repeatedParts" :key="index">
          <span>{{ part }}</span>
          <span class="text-[#9AE600]"> • </span>
        </template>
      </div>
    </div>
  </section>
</template>

<style scoped>
@keyframes scroll {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-50%);
  }
}

.animate-scroll {
  animation: scroll 30s linear infinite;
}
</style>
