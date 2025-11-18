<script setup lang="ts">
interface Props {
  text: string
  defaultVelocity?: number
  class?: string
}

const props = withDefaults(defineProps<Props>(), {
  defaultVelocity: 5,
  class: ''
})

const baseX1 = ref(0)
const baseX2 = ref(0)
const lastScrollY = ref(0)
const scrollVelocity = ref(0)
const directionFactor = ref(1)
const animationFrameId = ref<number>()

const repetitions = ref(3)
const containerRef1 = ref<HTMLDivElement>()
const containerRef2 = ref<HTMLDivElement>()
const textRef = ref<HTMLSpanElement>()

// Calcula número de repetições necessárias
const calculateRepetitions = () => {
  if (containerRef1.value && textRef.value) {
    const containerWidth = containerRef1.value.offsetWidth
    const textWidth = textRef.value.offsetWidth
    repetitions.value = Math.ceil(containerWidth / textWidth) + 2
  }
}

// Função wrap para criar loop infinito
const wrap = (min: number, max: number, v: number) => {
  const rangeSize = max - min
  return ((((v - min) % rangeSize) + rangeSize) % rangeSize) + min
}

// Calcula velocidade do scroll
const handleScroll = () => {
  const currentScrollY = window.scrollY
  const velocity = currentScrollY - lastScrollY.value
  scrollVelocity.value = velocity
  lastScrollY.value = currentScrollY

  // Atualiza direção baseada na velocidade do scroll
  if (velocity < 0) {
    directionFactor.value = -1
  } else if (velocity > 0) {
    directionFactor.value = 1
  }
}

// Smooth velocity (simula useSpring do framer-motion)
const smoothedVelocity = computed(() => {
  return scrollVelocity.value * 0.05 // Damping effect
})

// Animation loop
const animate = (timestamp: number, lastTime: number = 0) => {
  const delta = timestamp - lastTime

  // Movimento base
  let moveBy = directionFactor.value * props.defaultVelocity * (delta / 1000)

  // Adiciona efeito da velocidade do scroll
  const velocityFactor = Math.min(Math.abs(smoothedVelocity.value) / 100, 5)
  moveBy += directionFactor.value * moveBy * velocityFactor

  // Atualiza posições
  baseX1.value = wrap(-100 / repetitions.value, 0, baseX1.value + moveBy)
  baseX2.value = wrap(-100 / repetitions.value, 0, baseX2.value - moveBy) // Direção oposta

  // Decay da velocidade
  scrollVelocity.value *= 0.95

  animationFrameId.value = requestAnimationFrame((time) => animate(time, timestamp))
}

onMounted(() => {
  calculateRepetitions()
  window.addEventListener('resize', calculateRepetitions)
  window.addEventListener('scroll', handleScroll, { passive: true })

  lastScrollY.value = window.scrollY
  animationFrameId.value = requestAnimationFrame((time) => animate(time, 0))
})

onUnmounted(() => {
  window.removeEventListener('resize', calculateRepetitions)
  window.removeEventListener('scroll', handleScroll)
  if (animationFrameId.value) {
    cancelAnimationFrame(animationFrameId.value)
  }
})
</script>

<template>
  <section class="relative w-full">
    <!-- Primeira linha (direção positiva) -->
    <div ref="containerRef1" class="w-full overflow-hidden whitespace-nowrap">
      <div
        class="inline-block"
        :class="props.class"
        :style="{ transform: `translateX(${baseX1}%)` }"
      >
        <span
          v-for="i in repetitions"
          :key="`line1-${i}`"
          :ref="i === 1 ? (el) => textRef = el as HTMLSpanElement : undefined"
        >
          {{ text }}&nbsp;
        </span>
      </div>
    </div>

    <!-- Segunda linha (direção negativa) -->
    <div ref="containerRef2" class="w-full overflow-hidden whitespace-nowrap">
      <div
        class="inline-block"
        :class="props.class"
        :style="{ transform: `translateX(${baseX2}%)` }"
      >
        <span v-for="i in repetitions" :key="`line2-${i}`">
          {{ text }}&nbsp;
        </span>
      </div>
    </div>
  </section>
</template>
