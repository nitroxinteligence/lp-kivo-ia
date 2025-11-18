<script setup lang="ts">
const year = new Date().getFullYear()

const company = [
  {
    title: 'Como funciona',
    href: '#'
  },
  {
    title: 'Integrações',
    href: '#'
  },
  {
    title: 'Por quê Kivo IA',
    href: '#'
  },
  {
    title: 'Política de Privacidade',
    href: '#'
  },
  {
    title: 'Termos de Uso',
    href: '#'
  }
]

const socialLinks = [
  {
    icon: 'i-lucide-instagram',
    link: '#'
  },
  {
    icon: 'i-lucide-linkedin',
    link: '#'
  }
]
</script>

<template>
  <footer class="relative">
    <div class="bg-[radial-gradient(35%_80%_at_30%_0%,--theme(--color-foreground/.1),transparent)] mx-auto max-w-4xl md:border-x md:border-[#27272A]">
      <div class="bg-[#27272A] absolute inset-x-0 h-px w-full" />
      <div class="grid max-w-4xl grid-cols-1 md:grid-cols-12 gap-6 p-4">
        <div class="col-span-1 md:col-span-6 flex flex-col gap-5">
          <a href="#" class="w-max opacity-25">
            <UIcon name="i-lucide-grid-2x2-plus" class="size-8" />
          </a>
          <p class="text-muted-foreground max-w-sm font-mono text-sm text-balance">
            KIVO IA. Mais vendas. Menos custos. Atendimento em minutos.
          </p>
          <div class="flex gap-2">
            <a
              v-for="(item, i) in socialLinks"
              :key="i"
              class="hover:bg-accent rounded-md border border-[#27272A] p-1.5"
              target="_blank"
              :href="item.link"
            >
              <UIcon :name="item.icon" class="size-4" style="color: #27272A" />
            </a>
          </div>
        </div>
        <div class="col-span-1 md:col-span-6 md:col-start-11 w-full md:flex md:justify-end">
          <div class="w-full md:w-auto">
            <span class="text-muted-foreground mb-1 text-xs">Seções</span>
            <div class="flex flex-col gap-1">
              <a
                v-for="({ href, title }, i) in company"
                :key="i"
                class="w-max py-1 text-sm duration-200 hover:underline"
                style="color: #9F9FA9"
                :href="href"
              >
                {{ title }}
              </a>
            </div>
          </div>
        </div>
      </div>
      <div class="bg-[#27272A] absolute inset-x-0 h-px w-full" />
      <div class="flex max-w-4xl flex-col justify-between gap-2 pt-2 pb-5">
        <p class="text-center font-thin" style="color: #27272A">
          © KIVO IA. Todos os direitos reservados {{ year }}
        </p>
      </div>
    </div>
  </footer>
</template>
