<script setup lang="ts">
interface Props {
  to?: string
  size?: 'sm' | 'md' | 'lg' | 'xl'
  external?: boolean
  target?: string
}

const { to, size, external, target } = withDefaults(defineProps<Props>(), {
  to: '#',
  size: 'xl',
  external: false,
  target: '_self'
})
</script>

<template>
  <NuxtLink :to="to" :external="external" :target="target" class="custom-cta-button-wrapper">
    <button
      :class="[
        'custom-cta-button',
        'relative overflow-hidden',
        'inline-flex items-center justify-center',
        'px-6 py-3',
        'rounded-lg',
        'font-semibold',
        'text-white',
        'text-base sm:text-lg',
        'transition-all duration-300',
        'focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2',
        {
          'px-4 py-2': size === 'sm',
          'px-5 py-2.5': size === 'md',
          'px-6 py-3': size === 'lg',
          'px-8 py-4': size === 'xl'
        }
      ]"
      style="background: linear-gradient(135deg, #506D21 0%, #9AE600 50%, #ABC86F 100%)"
    >
      <!-- Texto do botão -->
      <span class="button-text flex items-center gap-3 transition-all duration-300">
        <span class="text-content">
          <slot />
        </span>

        <!-- Seta minimalista -->
        <svg
          class="arrow-icon w-5 h-5 transition-all duration-300"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M17 8l4 4m0 0l-4 4m4-4H3"
          />
        </svg>
      </span>

      <!-- Seta centralizada (aparece no hover) -->
      <span class="arrow-center absolute inset-0 flex items-center justify-center opacity-0 transition-all duration-300">
        <svg
          class="w-6 h-6"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M17 8l4 4m0 0l-4 4m4-4H3"
          />
        </svg>
      </span>
    </button>
  </NuxtLink>
</template>

<style scoped>
.custom-cta-button-wrapper {
  display: inline-block;
}

.custom-cta-button {
  position: relative;
}

/* Estado normal */
.custom-cta-button .button-text {
  opacity: 1;
  transform: translateX(0);
}

.custom-cta-button .arrow-center {
  opacity: 0;
  transform: scale(0.8);
}

/* Estado hover */
.custom-cta-button:hover .button-text {
  opacity: 0;
  transform: translateX(-10px);
}

.custom-cta-button:hover .arrow-center {
  opacity: 1;
  transform: scale(1);
}

/* Animação da seta no hover */
.custom-cta-button:hover .arrow-icon {
  transform: translateX(5px);
}
</style>
