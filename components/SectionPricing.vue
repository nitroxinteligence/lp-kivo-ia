<script setup lang="ts">
const isYearly = ref(false)

const plans = [
  {
    name: 'Starter',
    description: 'Ideal para pequenas empresas e startups começando com IA',
    price: 299,
    yearlyPrice: 2990,
    popular: false,
    features: [
      'Até 500 atendimentos/mês',
      'Integração WhatsApp',
      'Qualificação automática de leads',
      'Relatórios básicos',
      'Suporte por email'
    ]
  },
  {
    name: 'Business',
    description: 'Melhor custo-benefício para empresas em crescimento',
    price: 799,
    yearlyPrice: 7990,
    popular: true,
    features: [
      'Até 2.000 atendimentos/mês',
      'Tudo do Starter, mais:',
      'Integração com CRM',
      'Automação de propostas e contratos',
      'Envio automático de boletos',
      'Gestão de sinistros com IA',
      'Relatórios avançados',
      'Suporte prioritário'
    ]
  },
  {
    name: 'Enterprise',
    description: 'Solução completa para operações de grande escala',
    price: 1999,
    yearlyPrice: 19990,
    popular: false,
    features: [
      'Atendimentos ilimitados',
      'Tudo do Business, mais:',
      'API dedicada',
      'Customizações avançadas',
      'Múltiplas integrações',
      'Gerente de conta dedicado',
      'SLA garantido',
      'Treinamento personalizado'
    ]
  }
]

const formatPrice = (price: number) => {
  return new Intl.NumberFormat('pt-BR', {
    style: 'currency',
    currency: 'BRL',
    minimumFractionDigits: 0,
    maximumFractionDigits: 0
  }).format(price)
}
</script>

<template>
  <section class="relative overflow-hidden bg-gradient-to-b from-[#000000] to-[#161616] py-24">
    <!-- Background Effects -->
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-[800px] h-[800px] bg-lime-500/10 rounded-full blur-[120px]" />
      <div class="absolute bottom-0 right-0 w-[600px] h-[600px] bg-lime-500/5 rounded-full blur-[100px]" />
    </div>

    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header -->
      <div class="text-center mb-16 space-y-4">
        <h2 class="text-4xl md:text-5xl font-bold text-white">
          Planos que funcionam para seu negócio
        </h2>
        <p class="text-lg text-gray-400 max-w-2xl mx-auto">
          Escolha o plano ideal para transformar sua operação com IA
        </p>

        <!-- Toggle Mensal/Anual -->
        <div class="flex items-center justify-center gap-4 pt-8">
          <span :class="['text-sm font-medium transition-colors', !isYearly ? 'text-white' : 'text-gray-500']">
            Mensal
          </span>

          <button
            class="relative w-14 h-7 bg-gray-700 rounded-full transition-colors duration-300 focus:outline-none focus:ring-2 focus:ring-lime-500 focus:ring-offset-2 focus:ring-offset-gray-900"
            :class="{ 'bg-lime-600': isYearly }"
            @click="isYearly = !isYearly"
          >
            <span
              class="absolute top-0.5 left-0.5 w-6 h-6 bg-white rounded-full shadow-lg transform transition-transform duration-300"
              :class="{ 'translate-x-7': isYearly }"
            />
          </button>

          <span :class="['text-sm font-medium transition-colors', isYearly ? 'text-white' : 'text-gray-500']">
            Anual
            <span class="ml-1 text-xs text-lime-400">(Economize 17%)</span>
          </span>
        </div>
      </div>

      <!-- Pricing Cards -->
      <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
        <div
          v-for="(plan, index) in plans"
          :key="plan.name"
          class="relative group"
          :style="{ animationDelay: `${index * 100}ms` }"
        >
          <!-- Popular Badge -->
          <div
            v-if="plan.popular"
            class="absolute -top-4 left-1/2 -translate-x-1/2 z-10"
          >
            <div class="bg-gradient-to-r from-lime-500 to-lime-600 text-black text-xs font-bold px-4 py-1 rounded-full shadow-lg">
              MAIS POPULAR
            </div>
          </div>

          <UCard
            :class="[
              'h-full transition-all duration-300',
              plan.popular
                ? 'border-2 border-lime-500 shadow-xl shadow-lime-500/20 scale-105'
                : 'border border-gray-800 hover:border-gray-700 hover:shadow-lg',
              plan.popular ? 'bg-gray-900/90' : 'bg-gray-900/50'
            ]"
          >
            <!-- Plan Header -->
            <div class="text-center mb-8 p-6 sm:p-8">
              <h3 class="text-2xl font-bold text-white mb-2">{{ plan.name }}</h3>
              <p class="text-sm text-gray-400 mb-6">{{ plan.description }}</p>

              <div class="mb-6">
                <div class="flex items-baseline justify-center">
                  <span class="text-5xl font-bold text-white">
                    {{ formatPrice(isYearly ? plan.yearlyPrice : plan.price) }}
                  </span>
                  <span class="text-gray-400 ml-2">
                    /{{ isYearly ? 'ano' : 'mês' }}
                  </span>
                </div>
              </div>

              <UButton
                :color="plan.popular ? 'primary' : 'neutral'"
                :variant="plan.popular ? 'solid' : 'outline'"
                size="lg"
                block
                class="mb-8"
              >
                Começar Agora
              </UButton>
            </div>

            <!-- Features List -->
            <div class="space-y-4 border-t border-gray-800 pt-6">
              <div
                v-for="(feature, idx) in plan.features"
                :key="idx"
                class="flex items-start gap-3"
              >
                <div class="mt-1 flex-shrink-0">
                  <div
                    :class="[
                      'w-5 h-5 rounded-full flex items-center justify-center',
                      plan.popular ? 'bg-lime-500/20' : 'bg-gray-800'
                    ]"
                  >
                    <svg
                      class="w-3 h-3"
                      :class="plan.popular ? 'text-lime-400' : 'text-gray-400'"
                      fill="none"
                      stroke="currentColor"
                      viewBox="0 0 24 24"
                    >
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7" />
                    </svg>
                  </div>
                </div>
                <span
                  :class="[
                    'text-sm',
                    feature.includes('Tudo do') ? 'font-semibold text-white' : 'text-gray-300'
                  ]"
                >
                  {{ feature }}
                </span>
              </div>
            </div>
          </UCard>
        </div>
      </div>

      <!-- Footer Note -->
      <div class="text-center mt-16">
        <p class="text-sm text-gray-400">
          Todos os planos incluem 14 dias de teste grátis • Cancele quando quiser • Sem multa
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.group {
  animation: fadeInUp 0.6s ease-out forwards;
  opacity: 0;
}
</style>
