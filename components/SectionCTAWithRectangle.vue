<script setup lang="ts">
// Props baseadas no código original
const badge = {
  text: 'Comece Agora'
}

const title = 'Pronto para transformar sua operação?'
const description = 'Agende uma reunião e descubra como a Kivo IA pode aumentar suas vendas e reduzir custos.'

const action = {
  text: 'Agendar reunião com a KIVO IA',
  href: '/#agendar',
  variant: 'solid' as const
}

const withGlow = true
</script>

<template>
  <section class="overflow-hidden pt-0 md:pt-0">
    <div class="relative mx-auto flex max-w-container flex-col items-center gap-6 px-8 py-12 text-center sm:gap-8 md:py-24">
      <!-- Badge -->
      <UBadge
        v-if="badge"
        variant="outline"
        class="opacity-0 animate-fade-in-up delay-100"
      >
        <span class="text-muted-foreground">{{ badge.text }}</span>
      </UBadge>

      <!-- Title -->
      <h2 class="text-3xl font-semibold sm:text-5xl opacity-0 animate-fade-in-up delay-200">
        {{ title }}
      </h2>

      <!-- Description -->
      <p v-if="description" class="text-muted-foreground opacity-0 animate-fade-in-up delay-300">
        {{ description }}
      </p>

      <!-- Action Button -->
      <UButton
        :to="action.href"
        :variant="action.variant"
        color="primary"
        size="lg"
        class="opacity-0 animate-fade-in-up delay-500"
      >
        {{ action.text }}
      </UButton>

      <!-- Glow Effect -->
      <div v-if="withGlow" class="fade-top-lg pointer-events-none absolute inset-0 rounded-2xl shadow-glow opacity-0 animate-scale-in delay-700" />
    </div>
  </section>
</template>

<style scoped>
/* Animações baseadas no código original */
@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes scale-in {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.animate-fade-in-up {
  animation: fade-in-up 0.6s ease-out forwards;
}

.animate-scale-in {
  animation: scale-in 0.8s ease-out forwards;
}

.delay-100 {
  animation-delay: 100ms;
}

.delay-200 {
  animation-delay: 200ms;
}

.delay-300 {
  animation-delay: 300ms;
}

.delay-500 {
  animation-delay: 500ms;
}

.delay-700 {
  animation-delay: 700ms;
}

/* Glow effect */
.shadow-glow {
  box-shadow:
    0 0 50px rgba(163, 230, 53, 0.3),
    0 0 100px rgba(163, 230, 53, 0.2),
    0 0 150px rgba(163, 230, 53, 0.1);
}

.fade-top-lg {
  background: radial-gradient(
    ellipse 80% 50% at 50% 0%,
    rgba(163, 230, 53, 0.15),
    transparent
  );
}

.max-w-container {
  max-width: 1280px;
}

.text-muted-foreground {
  color: rgb(161, 161, 170);
}
</style>
