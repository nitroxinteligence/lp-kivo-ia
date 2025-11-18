<script setup lang="ts">
import { section7 } from '~/content/copy'
</script>

<template>
  <UPageSection :title="section7.title" class="bg-default">
    <div class="mt-6">
      <UPageList>
        <ul class="space-y-3">
          <li v-for="(item, i) in section7.items" :key="i" class="text-default">{{ item }}</li>
        </ul>
      </UPageList>
    </div>
    <p class="mt-8 text-muted text-center">{{ section7.support }}</p>
  </UPageSection>
</template>
