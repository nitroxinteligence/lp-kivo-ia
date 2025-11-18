<script setup lang="ts">
const sectionRef = ref<HTMLElement | null>(null)
const scrollY = ref(0)

const handleScroll = () => {
  if (sectionRef.value) {
    const sectionTop = sectionRef.value.offsetTop
    const relativeScroll = window.scrollY - sectionTop
    scrollY.value = Math.max(0, relativeScroll)
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

// Progresso da revelação (0 a 1)
// Mobile: 600px | Desktop: 800px de scroll para revelar completamente
const scrollDistance = computed(() => {
  if (typeof window === 'undefined') return 800
  return window.innerWidth < 768 ? 600 : 800
})
const revealProgress = computed(() => Math.min(scrollY.value / scrollDistance.value, 1))

// Clip-path para revelar o texto da esquerda para direita
const clipPath = computed(() => {
  const percentage = revealProgress.value * 100
  return `inset(0 ${100 - percentage}% 0 0)`
})
</script>

<template>
  <section ref="sectionRef" class="bg-default min-h-[250vh] md:min-h-[200vh] relative">
    <div class="h-screen flex items-center justify-center sticky top-0 [position:-webkit-sticky]">
      <UContainer>
        <div class="relative px-6 max-w-5xl mx-auto">
          <!-- Texto base (cinza/invisível) -->
          <h2 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold text-center text-muted/30 leading-[1.2] text-balance">
            Em 7 dias, sua operação rodando com IA real
          </h2>

          <!-- Texto revelado (gradiente/destaque) -->
          <h2
            class="absolute inset-0 text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-bold text-center bg-gradient-to-r from-primary via-primary to-primary bg-clip-text text-transparent leading-[1.2] will-change-[clip-path] text-balance"
            :style="{ clipPath }"
          >
            Em 7 dias, sua operação rodando com IA real
          </h2>
        </div>

        <!-- Indicador de progresso -->
        <div class="mt-16 flex justify-center">
          <div class="w-48 h-1 bg-muted/20 rounded-full overflow-hidden">
            <div
              class="h-full bg-primary transition-all duration-300"
              :style="{ width: `${revealProgress * 100}%` }"
            />
          </div>
        </div>

        <!-- Texto de instrução -->
        <p
          class="mt-8 text-center text-muted transition-opacity duration-500"
          :class="revealProgress < 1 ? 'opacity-100' : 'opacity-0'"
        >
          Continue rolando para revelar
        </p>
      </UContainer>
    </div>
  </section>
</template>
