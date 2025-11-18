<script setup lang="ts">
const sectionRef = ref<HTMLElement | null>(null)
const scrollY = ref(0)
const isMobile = ref(false)

const handleScroll = () => {
  if (sectionRef.value) {
    const sectionTop = sectionRef.value.offsetTop
    const relativeScroll = window.scrollY - sectionTop
    scrollY.value = Math.max(0, relativeScroll)
  }
}

const checkMobile = () => {
  isMobile.value = window.innerWidth < 768
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  window.addEventListener('resize', checkMobile)
  checkMobile()
  handleScroll() // Initial calculation
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
  window.removeEventListener('resize', checkMobile)
})

// Ajuste progressivo: mais scroll necessário no mobile para compensar altura menor
const scrollDistance = computed(() => isMobile.value ? 400 : 500)
const animationProgress = computed(() => Math.min(scrollY.value / scrollDistance.value, 1))

// Raio máximo responsivo: menor no mobile para não ultrapassar viewport
const maxRadius = computed(() => {
  if (typeof window === 'undefined') return 120
  const vw = window.innerWidth
  if (vw < 640) return 145  // sm: raio otimizado para ícones próximos mas respiráveis
  if (vw < 768) return 140  // md: raio intermediário
  if (vw < 1024) return 220 // lg: raio maior
  return 280 // desktop: raio completo
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

const getTransform = (angle: number) => {
  const x = expandRadius.value * Math.cos(angle)
  const y = expandRadius.value * Math.sin(angle)
  return `translate(${x}px, ${y}px)`
}
</script>

<template>
  <section ref="sectionRef" class="bg-[#000000] min-h-[350vh] sm:min-h-[320vh] md:min-h-[300vh] relative">
    <div class="absolute inset-0 pt-16 sm:pt-24 md:pt-32 pb-16 sm:pb-24 md:pb-32">
      <div class="h-screen flex items-center justify-center px-4 sm:px-6 md:px-8 sticky top-0">
        <UContainer>
          <div class="relative w-full flex items-center justify-center">
            <!-- Círculo externo -->
            <div
              :class="[
                'w-full max-w-[280px] sm:max-w-[400px] md:max-w-[500px] lg:max-w-[600px] aspect-square rounded-full flex items-center justify-center transition-all duration-500 mx-auto',
                scrollY > 300 ? 'ring-1 sm:ring-2 ring-primary/30' : ''
              ]"
            >
              <!-- Círculo intermediário -->
              <div
                :class="[
                  'w-[90%] aspect-square rounded-full flex items-center justify-center relative transition-all duration-500',
                  scrollY > 100 ? 'ring-1 sm:ring-2 ring-primary/20' : ''
                ]"
              >
                <!-- Círculo interno com gradiente -->
                <div class="w-[85%] aspect-square rounded-full bg-gradient-to-r from-primary/40 via-primary/60 to-primary/40 p-0.5 flex items-center justify-center relative">
                  <div class="w-full h-full rounded-full bg-[#000000] flex items-center justify-center relative overflow-visible">
                    <!-- Icon Cards -->
                    <div
                      v-for="(item, i) in icons"
                      :key="i"
                      class="absolute w-12 h-12 sm:w-14 sm:h-14 md:w-16 md:h-16 rounded-lg overflow-hidden bg-primary/10 backdrop-blur-sm border border-primary/20 shadow-lg transition-all duration-300 ease-out z-0 flex items-center justify-center group hover:bg-primary/20"
                      :style="{ transform: getTransform(item.angle) }"
                    >
                      <UIcon :name="item.icon" class="w-5 h-5 sm:w-6 sm:h-6 text-primary transition-transform duration-300 group-hover:scale-110" />
                    </div>

                    <!-- Central Text -->
                    <div
                      :class="[
                        'flex flex-col items-center justify-center relative z-20 transition-opacity duration-500 px-4 sm:px-6',
                        scrollY > 200 ? 'opacity-100' : 'opacity-0'
                      ]"
                    >
                      <h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl tracking-tight font-bold text-highlighted text-pretty text-center leading-[1.2] mb-3 sm:mb-4">
                        A Kivo IA<br>é entregue com
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
