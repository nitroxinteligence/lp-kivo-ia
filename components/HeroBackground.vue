<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Alturas simétricas dos pilares (porcentagem). Alto nas bordas, baixo no centro.
const pillars = [92, 84, 78, 70, 62, 54, 46, 34, 18, 34, 46, 54, 62, 70, 78, 84, 92]

// Estado para disparar animações quando o componente é montado
const isMounted = ref(false)

onMounted(() => {
  // Define isMounted como true após um pequeno delay para permitir que o componente renderize primeiro
  setTimeout(() => {
    isMounted.value = true
  }, 100)
})
</script>

<template>
  <div class="absolute inset-0 overflow-hidden">
    <!-- ================== BACKGROUND BASE ================== -->
    <!-- Fundo preto puro: #000000 -->
    <div
      aria-hidden="true"
      class="absolute inset-0 -z-40"
      :style="{
        background: '#000000'
      }"
    />

    <!-- ================== BACKGROUND OVERLAY ================== -->
    <!-- Gradientes elípticos luminosos adaptados para verde lime -->
    <div
      aria-hidden="true"
      class="absolute inset-0 -z-30"
      :style="{
        backgroundImage: [
          // Cúpula/banda central principal (ligeiramente abaixo do centro) - verde lime
          'radial-gradient(80% 55% at 50% 52%, rgba(163,230,53,0.35) 0%, rgba(101,163,13,0.38) 27%, rgba(20,40,15,0.32) 47%, rgba(15,25,15,0.40) 60%, rgba(8,12,8,0.92) 78%, transparent 88%)',
          // Varredura quente do topo esquerdo - verde claro
          'radial-gradient(85% 60% at 14% 0%, rgba(190,242,100,0.50) 0%, rgba(132,204,22,0.45) 30%, transparent 64%)',
          // Borda fria no topo direito - verde azulado
          'radial-gradient(70% 50% at 86% 22%, rgba(52,211,153,0.35) 0%, transparent 55%)',
          // Vinheta suave no topo
          'linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0) 40%)',
        ].join(','),
      }"
    />

    <!-- Vinheta nos cantos para contraste extra -->
    <div
      aria-hidden="true"
      class="absolute inset-0 -z-20 bg-[radial-gradient(140%_120%_at_50%_0%,transparent_60%,rgba(0,0,0,0.85))]"
    />

    <!-- Sobreposição de grade: colunas verticais + arcos horizontais sutis curvos -->
    <div
      aria-hidden="true"
      class="pointer-events-none absolute inset-0 -z-10 mix-blend-screen opacity-30"
      :style="{
        backgroundImage: [
          // Linhas de grade verticais (maiores e menores)
          'repeating-linear-gradient(90deg, rgba(163,230,53,0.12) 0 1px, transparent 1px 96px)',
          'repeating-linear-gradient(90deg, rgba(163,230,53,0.06) 0 1px, transparent 1px 24px)',
          // Arcos horizontais curvos via gradiente radial elíptico repetido
          'repeating-radial-gradient(80% 55% at 50% 52%, rgba(163,230,53,0.10) 0 1px, transparent 1px 120px)'
        ].join(','),
        backgroundBlendMode: 'screen',
      }"
    />

    <!-- ================== FOREGROUND ================== -->
    <!-- Brilho retangular central inferior com animação de pulso -->
    <div
      class="pointer-events-none absolute bottom-[128px] left-1/2 z-0 h-36 w-28 -translate-x-1/2 rounded-md bg-gradient-to-b from-lime-400/60 via-lime-300/40 to-transparent animate-pulse-subtle"
    />

    <!-- Silhueta de pilares escalonados -->
    <div class="pointer-events-none absolute inset-x-0 bottom-0 z-0 h-[54vh]">
      <!-- Fade escuro -->
      <div class="absolute inset-0 bg-gradient-to-t from-black via-black/90 to-transparent" />
      <!-- Barras -->
      <div class="absolute inset-x-0 bottom-0 flex h-full items-end gap-px px-[2px]">
        <div
          v-for="(h, i) in pillars"
          :key="i"
          class="flex-1 bg-black transition-all duration-1000 ease-in-out"
          :style="{
            height: isMounted ? `${h}%` : '0%',
            transitionDelay: `${Math.abs(i - Math.floor(pillars.length / 2)) * 60}ms`
          }"
        />
      </div>
    </div>
  </div>
</template>

<style scoped>
@keyframes pulse-subtle {
  0%, 100% {
    opacity: 0.6;
    transform: translateX(-50%) scale(1);
  }
  50% {
    opacity: 0.8;
    transform: translateX(-50%) scale(1.03);
  }
}

.animate-pulse-subtle {
  animation: pulse-subtle 6s ease-in-out infinite;
}
</style>
