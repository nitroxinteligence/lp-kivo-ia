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
  nextTick(() => {
    handleScroll() // Initial calculation
    window.addEventListener('scroll', handleScroll)
  })
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

// Desktop configuration
const scrollDistance = 500
const animationProgress = computed(() => Math.min(scrollY.value / scrollDistance, 1))

// Desktop radius (220-280px max)
const maxRadius = computed(() => {
  if (typeof window === 'undefined') return 220
  const vw = window.innerWidth
  if (vw < 1024) return 220  // lg
  if (vw < 1280) return 250  // xl
  return 280                 // 2xl+
})

const expandRadius = computed(() => animationProgress.value * maxRadius.value)

const icons = [
  { angle: 0, icon: 'i-lucide-brain', label: 'IA' },
  { angle: Math.PI / 4, icon: 'i-lucide-zap', label: 'Automação' },
  { angle: Math.PI / 2, icon: 'i-lucide-users', label: 'Clientes' },
  { angle: (3 * Math.PI) / 4, icon: 'i-lucide-shield-check', label: 'Proteção' },
  { angle: Math.PI, icon: 'i-lucide-trending-up', label: 'Crescimento' },
  { angle: (5 * Math.PI) / 4, icon: 'i-lucide-sparkles', label: 'Inovação' },
  { angle: (3 * Math.PI) / 2, icon: 'i-lucide-cpu', label: 'Tecnologia' },
  { angle: (7 * Math.PI) / 4, icon: 'i-lucide-rocket', label: 'Sucesso' }
]

// CRIAR COMPUTED PARA CADA ÍCONE - CORREÇÃO DE REATIVIDADE
const iconTransforms = computed(() => {
  return icons.map(item => ({
    ...item,
    transform: `translate(${expandRadius.value * Math.cos(item.angle)}px, ${expandRadius.value * Math.sin(item.angle)}px)`
  }))
})
</script>

<template>
  <!-- DESKTOP VERSION ONLY -->
  <section ref="sectionRef" class="hidden md:block bg-[#000000] min-h-[300vh] relative">
    <div class="absolute inset-0 pt-24 md:pt-32 pb-24 md:pb-32">
      <div class="h-screen flex items-center justify-center px-6 md:px-8 sticky top-0">
        <UContainer>
          <div class="relative w-full flex items-center justify-center">
            <!-- Outer circle - larger for desktop -->
            <div
              :class="[
                'w-full md:max-w-[500px] lg:max-w-[600px] xl:max-w-[700px] aspect-square rounded-full flex items-center justify-center transition-all duration-500 mx-auto',
                animationProgress > 0.6 ? 'ring-2 ring-primary/30' : ''
              ]"
            >
              <!-- Middle circle -->
              <div
                :class="[
                  'w-[90%] aspect-square rounded-full flex items-center justify-center relative transition-all duration-500',
                  animationProgress > 0.3 ? 'ring-2 ring-primary/20' : ''
                ]"
              >
                <!-- Inner circle with gradient -->
                <div class="w-[85%] aspect-square rounded-full bg-gradient-to-r from-primary/40 via-primary/60 to-primary/40 p-0.5 flex items-center justify-center relative">
                  <div class="w-full h-full rounded-full bg-[#000000] flex items-center justify-center relative overflow-visible">
                    <!-- Icon Cards - Desktop sizes - USANDO COMPUTED! -->
                    <div
                      v-for="(item, i) in iconTransforms"
                      :key="i"
                      class="absolute md:w-14 md:h-14 lg:w-16 lg:h-16 xl:w-18 xl:h-18 rounded-lg overflow-hidden bg-primary/10 backdrop-blur-sm border border-primary/20 shadow-lg transition-all duration-300 ease-out z-0 flex items-center justify-center group hover:bg-primary/20"
                      :style="{ transform: item.transform }"
                    >
                      <UIcon :name="item.icon" class="md:w-6 md:h-6 lg:w-7 lg:h-7 text-primary transition-transform duration-300 group-hover:scale-110" />
                    </div>

                    <!-- Central Text - Desktop version without line break -->
                    <div
                      :class="[
                        'flex flex-col items-center justify-center relative z-20 transition-opacity duration-500 px-4 sm:px-6',
                        animationProgress > 0.4 ? 'opacity-100' : 'opacity-0'
                      ]"
                    >
                      <h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl tracking-tight font-bold text-highlighted text-balance text-center leading-[1.2] md:leading-[1.3] mb-3 sm:mb-4">
                        A Kivo IA é entregue com...
                      </h2>

                      <p class="text-sm sm:text-base md:text-lg text-muted text-pretty text-center max-w-xs sm:max-w-md font-normal">
                        Setup rápido, treinamento do time e garantia de 60 dias para validar resultado.
                      </p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </UContainer>
      </div>
    </div>
  </section>
</template>