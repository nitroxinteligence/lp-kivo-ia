<script setup lang="ts">
const sectionRef = ref<HTMLElement | null>(null)
const scrollY = ref(0)

// Logs removidos na versão final - descomentar para debug
// const logDebug = (...args: any[]) => console.log(...args)

const handleScroll = () => {
  console.log('🔴 MOBILE handleScroll CHAMADO')
  console.log('📱 sectionRef existe?', !!sectionRef.value)
  console.log('📊 scrollY ANTES:', scrollY.value)

  if (sectionRef.value) {
    const sectionTop = sectionRef.value.offsetTop
    const relativeScroll = window.scrollY - sectionTop
    scrollY.value = Math.max(0, relativeScroll)

    console.log('✅ sectionTop:', sectionTop)
    console.log('✅ window.scrollY:', window.scrollY)
    console.log('✅ relativeScroll:', relativeScroll)
    console.log('✅ scrollY DEPOIS:', scrollY.value)
    console.log('🎯 animationProgress:', animationProgress.value)
    console.log('📏 expandRadius:', expandRadius.value)
  } else {
    console.log('❌ sectionRef é NULL!')
  }
}

onMounted(() => {
  console.log('🚀 MOBILE COMPONENT MOUNTED')
  console.log('📱 Window width:', window.innerWidth)
  console.log('📱 Viewport < 768?', window.innerWidth < 768)
  console.log('📱 sectionRef no mount:', sectionRef.value)

  // GARANTIR QUE ESTAMOS NO CLIENT
  if (typeof window !== 'undefined') {
    nextTick(() => {
      console.log('⏭️ nextTick executado')
      console.log('📱 sectionRef no nextTick:', sectionRef.value)

      // FORÇAR ATUALIZAÇÃO INICIAL
      if (sectionRef.value) {
        handleScroll() // Initial calculation
        window.addEventListener('scroll', handleScroll)
        console.log('✅ Scroll listener adicionado')

        // FORÇAR TRIGGER INICIAL
        setTimeout(() => {
          console.log('⏱️ Forçando handleScroll após 100ms')
          handleScroll()
        }, 100)
      } else {
        console.log('❌ sectionRef ainda é NULL no nextTick!')
      }
    })
  }
})

onUnmounted(() => {
  console.log('🔚 MOBILE COMPONENT UNMOUNTED')
  window.removeEventListener('scroll', handleScroll)
})

// Mobile configuration - AUMENTADO para mais tempo de animação
const scrollDistance = 500 // Aumentado de 350 para 500

// Mobile radius - EXPANDIDO AINDA MAIS para as laterais
const maxRadius = computed(() => {
  if (typeof window === 'undefined') return 145
  const vw = window.innerWidth
  if (vw < 375) return 135   // iPhone SE
  if (vw < 430) return 145   // iPhone Pro
  if (vw < 640) return 155   // sm
  return 165                 // max mobile
})

// Animation progress - SEM LOGS INTERNOS
const animationProgress = computed(() => Math.min(scrollY.value / scrollDistance, 1))

// Expand radius - SEM LOGS INTERNOS
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

// CRIAR COMPUTED PARA CADA ÍCONE - SOLUÇÃO DEFINITIVA!
const iconTransforms = computed(() => {
  return icons.map(item => ({
    ...item,
    transform: `translate(${expandRadius.value * Math.cos(item.angle)}px, ${expandRadius.value * Math.sin(item.angle)}px)`
  }))
})

// Monitor de reatividade - DEPOIS de todas as variáveis
watch(scrollY, (newValue, oldValue) => {
  console.log('🔄 scrollY MUDOU:', oldValue, '->', newValue)
})

watch(expandRadius, (newValue, oldValue) => {
  console.log('🔄 expandRadius MUDOU:', oldValue, '->', newValue)
})

// Watches para debug - DEPOIS de todas as variáveis
watchEffect(() => {
  console.log('📊 DEBUG VALORES:', {
    scrollY: scrollY.value,
    animationProgress: animationProgress.value,
    maxRadius: maxRadius.value,
    expandRadius: expandRadius.value
  })
})
</script>

<template>
  <!-- MOBILE VERSION ONLY -->
  <section ref="sectionRef" class="md:hidden bg-[#000000] min-h-[400vh] relative">
    <div class="absolute inset-0 pt-16 sm:pt-20 pb-16 sm:pb-20">
      <div class="h-screen flex items-center justify-center px-4 sm:px-6 sticky top-0 overflow-hidden">
        <UContainer>
          <div class="relative w-full flex items-center justify-center">
            <!-- Outer circle - smaller for mobile -->
            <div
              :class="[
                'w-full max-w-[280px] sm:max-w-[320px] aspect-square rounded-full flex items-center justify-center transition-all duration-500 mx-auto',
                animationProgress > 0.6 ? 'ring-1 ring-primary/30' : ''
              ]"
            >
              <!-- Middle circle -->
              <div
                :class="[
                  'w-[90%] aspect-square rounded-full flex items-center justify-center relative transition-all duration-500',
                  animationProgress > 0.3 ? 'ring-1 ring-primary/20' : ''
                ]"
              >
                <!-- Inner circle with gradient -->
                <div class="w-[85%] aspect-square rounded-full bg-gradient-to-r from-primary/40 via-primary/60 to-primary/40 p-0.5 flex items-center justify-center relative">
                  <div class="w-full h-full rounded-full bg-[#000000] flex items-center justify-center relative overflow-visible">
                    <!-- Icon Cards - Mobile sizes - USANDO COMPUTED! -->
                    <div
                      v-for="(item, i) in iconTransforms"
                      :key="i"
                      class="absolute w-10 h-10 sm:w-12 sm:h-12 rounded-lg overflow-hidden bg-primary/10 backdrop-blur-sm border border-primary/20 shadow-lg transition-all duration-300 ease-out z-0 flex items-center justify-center group hover:bg-primary/20"
                      :style="{ transform: item.transform }"
                    >
                      <UIcon :name="item.icon" class="w-4 h-4 sm:w-5 sm:h-5 text-primary transition-transform duration-300 group-hover:scale-110" />
                    </div>

                    <!-- Central Text - Mobile version with line break -->
                    <div
                      :class="[
                        'flex flex-col items-center justify-center relative z-20 transition-opacity duration-500 px-4 sm:px-6',
                        animationProgress > 0.4 ? 'opacity-100' : 'opacity-0'
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