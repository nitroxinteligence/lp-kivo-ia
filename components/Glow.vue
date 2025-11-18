<script setup lang="ts">
interface Props {
  variant?: 'top' | 'above' | 'bottom' | 'below' | 'center'
}

const props = withDefaults(defineProps<Props>(), {
  variant: 'top'
})

const variantClasses = {
  top: 'top-0',
  above: '-top-[128px]',
  bottom: 'bottom-0',
  below: '-bottom-[128px]',
  center: 'top-[50%]'
}

const positionClass = computed(() => variantClasses[props.variant])
const isCentered = computed(() => props.variant === 'center')
</script>

<template>
  <div :class="['absolute w-full', positionClass]">
    <div
      :class="[
        'absolute left-1/2 h-[256px] w-[60%] -translate-x-1/2 scale-[2.5] rounded-[50%] bg-[radial-gradient(ellipse_at_center,_hsla(var(--brand-foreground)/.5)_10%,_hsla(var(--brand-foreground)/0)_60%)] sm:h-[512px]',
        isCentered && '-translate-y-1/2'
      ]"
    />
    <div
      :class="[
        'absolute left-1/2 h-[128px] w-[40%] -translate-x-1/2 scale-[2] rounded-[50%] bg-[radial-gradient(ellipse_at_center,_hsla(var(--brand)/.3)_10%,_hsla(var(--brand-foreground)/0)_60%)] sm:h-[256px]',
        isCentered && '-translate-y-1/2'
      ]"
    />
  </div>
</template>
