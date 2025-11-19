<script setup lang="ts">
import { section3 } from '~/content/copy'

const cards = [
  {
    title: section3.subtitle,
    items: [],
    icon: 'i-lucide-x-circle'
  },
  {
    title: section3.text,
    items: section3.items,
    icon: 'i-lucide-check-circle'
  }
]
</script>

<template>
  <UPageSection class="bg-gradient-to-b from-[#000000] to-[#161616]">
    <UContainer>
      <h2 class="text-3xl sm:text-4xl lg:text-5xl tracking-tight font-bold text-highlighted text-pretty text-center leading-[48px]">
        {{ section3.title }}
      </h2>
      <p class="mt-6 text-base sm:text-lg text-muted text-pretty text-center max-w-3xl mx-auto font-normal">
        Compare o antes e depois:<br>veja como a IA transforma a eficiência operacional e os resultados da sua empresa.
      </p>
    </UContainer>

    <div class="mt-8 max-w-2xl mx-auto">
      <div class="grid grid-cols-1 gap-6">
        <UCard
          v-for="(card, i) in cards"
          :key="i"
          variant="subtle"
          :class="[
            'group transition-all duration-300',
            i === 0 ? '!ring-[#4A2124] hover:!ring-red-900' : '!ring-[#76ad00] hover:!ring-primary/50'
          ]"
        >
          <div class="flex flex-col gap-6 p-4">
            <div class="flex items-center gap-4">
              <div class="flex-shrink-0">
                <div
:class="[
                  'w-16 h-16 rounded-full flex items-center justify-center transition-colors duration-300',
                  i === 0 ? 'bg-red-500/10 group-hover:bg-red-500/20' : 'bg-primary/10 group-hover:bg-primary/20'
                ]">
                  <UIcon
                    :name="card.icon"
                    :class="[
                      'w-8 h-8',
                      i === 0 ? 'text-red-500' : 'text-primary'
                    ]"
                  />
                </div>
              </div>
              <h3
:class="[
                'text-highlighted',
                i === 0 ? 'text-base sm:text-lg font-medium' : 'text-xl sm:text-2xl font-bold'
              ]">{{ card.title }}</h3>
            </div>

            <ul v-if="card.items.length > 0" class="space-y-3">
              <li
                v-for="(item, j) in card.items"
                :key="j"
                class="flex items-start gap-3 text-default"
              >
                <UIcon
                  name="i-lucide-check"
                  class="w-5 h-5 flex-shrink-0 mt-0.5 text-primary"
                />
                <span class="text-sm sm:text-base font-medium leading-relaxed">{{ item }}</span>
              </li>
            </ul>
          </div>
        </UCard>
      </div>
    </div>
  </UPageSection>
</template>
