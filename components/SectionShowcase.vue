<script setup lang="ts">
</script>

<template>
  <UPageSection class="bg-default">
    <UContainer>
      <section class="min-h-screen w-full text-black dark:text-white px-8 py-16 md:px-16">
        <div class="mx-auto grid max-w-6xl items-center gap-12 md:grid-cols-2">
          <div class="relative mx-auto flex h-[28rem] md:h-[40rem] w-full max-w-[60rem] items-center justify-center overflow-hidden rounded-3xl">
            <div class="absolute -inset-10 flex items-center justify-center">
              <div
                class="h-[120%] w-[120%] rounded-[36px] blur-3xl opacity-80 animate-[spin_8s_linear_infinite]"
                style="background:
                  conic-gradient(
                    from 0deg,
                    #9AE600,
                    #c0ff38,
                    #e3ffa8,
                    #9AE600,
                    #78af00,
                    #e3ffa8
                  );"
              />
            </div>

            <div class="w-[85%] sm:w-full max-w-lg md:w-[340px] z-10 rounded-2xl border border-white/10 bg-black/85 shadow-2xl backdrop-blur-xl">
              <div class="p-4 md:p-5">
                <div class="mb-2 md:mb-3 flex items-center justify-between">
                  <span class="text-sm font-medium">KIVO IA</span>
                  <span class="text-xs text-zinc-400">87% de 100%</span>
                </div>
                <div class="mb-2 md:mb-3 h-1.5 w-full overflow-hidden rounded-full bg-white/10">
                  <div class="h-full w-[92%] rounded-full" style="background: linear-gradient(90deg, #78af00, #9AE600, #c0ff38)" />
                </div>
                <p class="text-xs text-zinc-400">
                  Planejando a sua IA com menos custos, mais vendas e em maior escala.
                </p>
                <a
                  href="https://wa.me/5511991943683?text=Ol%C3%A1!%20Vim%20pelo%20site%20da%20KIVO%20IA%20e%20gostaria%20de%20mais%20informa%C3%A7%C3%B5es"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="mt-3 md:mt-4 w-full rounded-lg text-white hover:opacity-90 px-4 py-2 inline-block text-center"
                  style="background-color: #9AE600"
                >
                  Agendar
                </a>
              </div>
            </div>
          </div>

          <div class="space-y-4">
            <h2 class="font-bold text-highlighted text-3xl sm:text-4xl lg:text-5xl leading-tight">
              Sua equipe perde tempo entre CRM, planilha, contrato, cobrança e sinistro?
              <span class="block mt-2 text-muted text-base sm:text-lg font-normal">A Kivo IA conecta tudo o que você já usa... WhatsApp, redes sociais e sistemas de gestão com automações que vendem, cobram e atendem de forma inteligente.</span>
            </h2>
          </div>
        </div>
      </section>
    </UContainer>
  </UPageSection>
</template>

<style scoped>
:root {
  --color-emerald-400: rgb(52 211 153);
  --color-cyan-400: rgb(34 211 238);
  --color-blue-500: rgb(59 130 246);
  --color-violet-600: rgb(124 58 237);
  --color-red-500: rgb(239 68 68);
  --color-sky-400: rgb(56 189 248);
}
</style>
