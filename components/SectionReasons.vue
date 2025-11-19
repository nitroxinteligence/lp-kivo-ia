<script setup lang="ts">
import { section5 } from '~/content/copy'

const stats = [
  {
    icon: 'i-lucide-trending-up',
    value: 40,
    description: '7 em cada 10 empresas que adotaram automação comercial aumentaram as vendas em até 40%'
  },
  {
    icon: 'i-lucide-piggy-bank',
    value: 35,
    description: 'Atendimentos digitais com IA reduziram o custo por cliente em até 35%'
  },
  {
    icon: 'i-lucide-zap',
    value: 70,
    description: 'O tempo de resposta ao sinistro caiu até 70% em operações automatizadas'
  }
]

</script>

<template>
  <UPageSection id="por-que-ia" class="bg-[#161616]">
    <UContainer>
      <h2 class="text-3xl sm:text-4xl lg:text-5xl tracking-tight font-bold text-highlighted text-pretty text-center leading-[48px]">{{ section5.title }}</h2>
      <p class="mt-6 text-base sm:text-lg text-muted text-pretty text-center max-w-3xl mx-auto font-normal">{{ section5.subtitle }}</p>
    </UContainer>

    <div class="mt-8 max-w-7xl mx-auto">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <UCard
          v-for="(stat, i) in stats"
          :key="i"
          variant="subtle"
          class="group hover:ring-primary/50 transition-all duration-300 !border !border-[#27272A]"
        >
          <div class="flex flex-col items-center text-center gap-4 p-4">
            <div class="flex-shrink-0">
              <div class="w-16 h-16 rounded-full bg-primary/10 flex items-center justify-center group-hover:bg-primary/20 transition-colors duration-300">
                <UIcon :name="stat.icon" class="w-8 h-8 text-primary" />
              </div>
            </div>
            <div class="space-y-2">
              <div class="text-5xl sm:text-6xl font-bold text-primary">
                {{ stat.value }}%
              </div>
              <p class="text-sm sm:text-base text-default font-medium leading-relaxed">
                {{ stat.description }}
              </p>
            </div>
          </div>
        </UCard>
      </div>
    </div>

    <div class="mt-8 flex justify-center">
      <UBadge
        :label="section5.note"
        leading-icon="i-lucide-globe"
        variant="outline"
        color="neutral"
        size="md"
        class="!bg-transparent !border-[#383838] !text-[#a8a8a8] !ring-[#383838] !rounded-[10px] [&>svg]:!text-[#a8a8a8]"
      />
    </div>
  </UPageSection>
</template>
