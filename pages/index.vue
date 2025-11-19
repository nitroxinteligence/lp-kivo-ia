<script setup lang="ts">
import SectionHero from '~/components/SectionHero.vue'
import SectionScenario from '~/components/SectionScenario.vue'
import SectionVelocityScroll from '~/components/SectionVelocityScroll.vue'
import SectionShowcase from '~/components/SectionShowcase.vue'
import SectionHow from '~/components/SectionHow.vue'
import SectionReasons from '~/components/SectionReasons.vue'
import SectionSavings from '~/components/SectionSavings.vue'
import SectionIntegrationsShowcase from '~/components/SectionIntegrationsShowcase.vue'
import SectionScrollReveal from '~/components/SectionScrollReveal.vue'
import SectionScrollAnimationMobile from '~/components/SectionScrollAnimationMobile.vue'
import SectionScrollAnimationDesktop from '~/components/SectionScrollAnimationDesktop.vue'
import SectionCTA from '~/components/SectionCTA.vue'
import Footer from '~/components/Footer.vue'
</script>

<template>
  <SectionHero />
  <SectionShowcase />
  <SectionScenario />
  <SectionVelocityScroll />
  <SectionHow />
  <SectionReasons />
  <SectionSavings />
  <SectionIntegrationsShowcase />
  <SectionScrollReveal />

  <!-- SEPARADOS: Mobile e Desktop -->
  <SectionScrollAnimationMobile />
  <SectionScrollAnimationDesktop />

  <SectionCTA />
  <Footer />
</template>
