<script setup lang="ts">
interface Props {
  class?: string
}

defineProps<Props>()
</script>

<template>
  <button
    class="shiny-button relative rounded-lg px-6 py-2 font-medium backdrop-blur-xl transition-shadow duration-300 ease-in-out hover:shadow dark:bg-[radial-gradient(circle_at_50%_0%,hsl(var(--primary)/10%)_0%,transparent_60%)] dark:hover:shadow-[0_0_20px_hsl(var(--primary)/10%)]"
    :class="$props.class"
  >
    <span
      class="relative block size-full text-sm uppercase tracking-wide text-[rgb(0,0,0,65%)] dark:font-light dark:text-[rgb(255,255,255,90%)]"
      style="mask-image: linear-gradient(-75deg,hsl(var(--primary)) calc(var(--x) + 20%),transparent calc(var(--x) + 30%),hsl(var(--primary)) calc(var(--x) + 100%))"
    >
      <slot />
    </span>
    <span
      style="mask: linear-gradient(rgb(0,0,0), rgb(0,0,0)) content-box,linear-gradient(rgb(0,0,0), rgb(0,0,0)); mask-composite: exclude;"
      class="absolute inset-0 z-10 block rounded-[inherit] bg-[linear-gradient(-75deg,hsl(var(--primary)/10%)_calc(var(--x)+20%),hsl(var(--primary)/50%)_calc(var(--x)+25%),hsl(var(--primary)/10%)_calc(var(--x)+100%))] p-px"
    />
  </button>
</template>

<style scoped>
.shiny-button {
  --x: 100%;
  animation: shiny-animation 4s infinite;
  transform-origin: center;
}

.shiny-button:active {
  animation: shiny-tap 0.2s ease-out;
}

@keyframes shiny-animation {
  0% {
    --x: 100%;
    scale: 0.8;
  }
  25% {
    scale: 1;
  }
  50% {
    --x: -100%;
  }
  75% {
    --x: -100%;
    scale: 1;
  }
  100% {
    --x: 100%;
    scale: 0.8;
  }
}

@keyframes shiny-tap {
  0% {
    scale: 1;
  }
  50% {
    scale: 0.95;
  }
  100% {
    scale: 1;
  }
}
</style>
