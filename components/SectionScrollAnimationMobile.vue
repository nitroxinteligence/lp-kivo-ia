<script setup lang="ts">
// Mobile radius - static values
const maxRadius = computed(() => {
  if (typeof window === 'undefined') return 145
  const vw = window.innerWidth
  if (vw < 375) return 135   // iPhone SE
  if (vw < 430) return 145   // iPhone Pro
  if (vw < 640) return 155   // sm
  return 165                 // max mobile
})

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

// Icons already expanded at full radius
const iconTransforms = computed(() => {
  return icons.map(item => ({
    ...item,
    transform: `translate(${maxRadius.value * Math.cos(item.angle)}px, ${maxRadius.value * Math.sin(item.angle)}px)`
  }))
})
</script>

<template>
  <!-- MOBILE VERSION ONLY -->
  <section class="md:hidden bg-[#000000] py-16 sm:py-20">
    <div class="flex items-center justify-center px-4 sm:px-6">
      <UContainer>
        <div class="relative w-full flex items-center justify-center">
          <!-- Outer circle - smaller for mobile -->
          <div class="w-full max-w-[280px] sm:max-w-[320px] aspect-square rounded-full flex items-center justify-center ring-1 ring-primary/30 mx-auto">
            <!-- Middle circle -->
            <div class="w-[90%] aspect-square rounded-full flex items-center justify-center relative ring-1 ring-primary/20">
              <!-- Inner circle with gradient -->
              <div class="w-[85%] aspect-square rounded-full bg-gradient-to-r from-primary/40 via-primary/60 to-primary/40 p-0.5 flex items-center justify-center relative">
                <div class="w-full h-full rounded-full bg-[#000000] flex items-center justify-center relative overflow-visible">
                  <!-- Icon Cards - Mobile sizes -->
                  <div
                    v-for="(item, i) in iconTransforms"
                    :key="i"
                    class="absolute w-10 h-10 sm:w-12 sm:h-12 rounded-lg overflow-hidden bg-primary/10 backdrop-blur-sm border border-primary/20 shadow-lg transition-all duration-300 ease-out z-0 flex items-center justify-center group hover:bg-primary/20"
                    :style="{ transform: item.transform }"
                  >
                    <UIcon :name="item.icon" class="w-4 h-4 sm:w-5 sm:h-5 text-primary transition-transform duration-300 group-hover:scale-110" />
                  </div>

                  <!-- Central Text - Mobile version with line break -->
                  <div class="flex flex-col items-center justify-center relative z-20 px-4 sm:px-6">
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
  </section>
</template>