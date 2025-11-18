<script setup lang="ts">
const integrations = [
  {
    title: 'HubSpot',
    description: 'CRM completo para vendas e marketing',
    icon: 'i-lucide-database',
    link: '#'
  },
  {
    title: 'Bitrix24',
    description: 'Plataforma de colaboração e CRM',
    icon: 'i-lucide-layers',
    link: '#'
  },
  {
    title: 'Salesforce',
    description: 'Líder mundial em CRM',
    icon: 'i-lucide-cloud',
    link: '#'
  },
  {
    title: 'WhatsApp Business',
    description: 'API oficial do WhatsApp',
    icon: 'i-lucide-message-circle',
    link: '#'
  },
  {
    title: 'ERP Financeiro',
    description: 'Sistemas de gestão empresarial',
    icon: 'i-lucide-receipt',
    link: '#'
  },
  {
    title: 'Plataformas de Cobrança',
    description: 'Integração com gateways de pagamento',
    icon: 'i-lucide-credit-card',
    link: '#'
  }
]
</script>

<template>
  <section id="integracoes" class="bg-gradient-to-b from-[#161616] to-[#000000]">
    <div class="py-32">
      <UContainer>
        <div class="mx-auto max-w-5xl px-6">
          <div class="text-center">
            <h2 class="text-balance text-3xl font-semibold md:text-4xl text-highlighted">
              Integramos a Kivo IA as suas principais ferramentas
            </h2>
            <p class="text-muted mt-6">
              Conecte-se perfeitamente com plataformas e serviços populares para otimizar seu fluxo de trabalho.
            </p>
          </div>

          <div class="mt-12 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
            <UCard
              v-for="(integration, i) in integrations"
              :key="i"
              variant="subtle"
              class="group hover:ring-primary/50 transition-all duration-300 !border !border-[#27272A]"
            >
              <div class="relative p-6">
                <div class="flex-shrink-0">
                  <div class="w-16 h-16 rounded-full bg-primary/10 flex items-center justify-center group-hover:bg-primary/20 transition-colors duration-300">
                    <UIcon :name="integration.icon" class="w-8 h-8 text-primary" />
                  </div>
                </div>

                <div class="space-y-2 py-6">
                  <h3 class="text-base font-medium text-default">{{ integration.title }}</h3>
                  <p class="text-muted line-clamp-2 text-sm">{{ integration.description }}</p>
                </div>
              </div>
            </UCard>
          </div>
        </div>
      </UContainer>
    </div>
  </section>
</template>
