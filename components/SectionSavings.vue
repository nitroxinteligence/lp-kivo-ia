<script setup lang="ts">
import { section6 } from '~/content/copy'

const cards = [
  {
    title: section6.card1.title,
    items: section6.card1.items,
    icon: 'i-lucide-x-circle'
  },
  {
    title: section6.card2.title,
    items: section6.card2.items,
    icon: 'i-lucide-check-circle'
  }
]
</script>

<template>
  <UPageSection class="bg-[#161616]">
    <UContainer>
      <h2 class="text-3xl sm:text-4xl lg:text-5xl tracking-tight font-bold text-highlighted text-pretty text-center leading-tight">
        {{ section6.title }}
      </h2>
    </UContainer>

    <div class="mt-8 max-w-7xl mx-auto">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
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
              <h3 class="text-xl sm:text-2xl font-bold text-highlighted">{{ card.title }}</h3>
            </div>

            <ul class="space-y-3">
              <li
                v-for="(item, j) in card.items"
                :key="j"
                class="flex items-start gap-3 text-default"
              >
                <UIcon
                  :name="i === 0 ? 'i-lucide-minus' : 'i-lucide-check'"
                  class="w-5 h-5 flex-shrink-0 mt-0.5"
                  :class="i === 0 ? 'text-muted' : 'text-primary'"
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
