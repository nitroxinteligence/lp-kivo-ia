## Pré-instalação
- Confirmar que a raiz do projeto (`LP - Kivo IA`) não possui Nuxt; vamos inicializar.

## Instalação de Nuxt (de acordo com https://ui.nuxt.com/docs/getting-started/installation/nuxt)
- Criar projeto Nuxt 3 na raiz:
  - `npx nuxi@latest init .`
  - `npm install`
- Executar dev para validar base:
  - `npm run dev`

## Instalação do Nuxt UI (https://ui.nuxt.com/docs)
- Adicionar o módulo Nuxt UI:
  - `npx nuxi@latest module add @nuxt/ui`
  - Alternativa manual (se necessário): instalar `@nuxt/ui` e adicionar em `nuxt.config.ts`:
    - `npm i -D @nuxt/ui`
    - Em `nuxt.config.ts`: `modules: ['@nuxt/ui']`
- Opcional: configurar tema em `app.config.ts` (cores primárias, tipografia).

## Estrutura de Projeto
- `layouts/default.vue`: cabeçalho (logo/brand + CTA) e rodapé.
- `pages/index.vue`: compõe todas as seções.
- `components/SectionHero.vue` (Seção 1)
- `components/SectionPainPoints.vue` (Seção 2)
- `components/SectionCurrentScenario.vue` (Seção 3)
- `components/SectionHowWorks.vue` (Seção 4)
- `components/SectionWhyIA.vue` (Seção 5)
- `components/SectionSavings.vue` (Seção 6)
- `components/SectionIntegrations.vue` (Seção 7)
- `components/SectionDelivery.vue` (Seção 8)
- `components/SectionCTA.vue` (Seção 9)
- `content/copy.ts`: textos centralizados da copy.

## Mapeamento da Copy → Nuxt UI
- Seção 1 (Hero): `UContainer`, `UHeading`, parágrafo, `UButton` (CTA principal).
- Seção 2 (Problema): blocos de texto com `UContainer`/`UCard`.
- Seção 3 (Cenário atual): bullets com `UList` e métricas em `UCard`.
- Seção 4 (Como funciona): `UGrid` com cartões (`UCard`) e `UIcon`.
- Seção 5 (Por que migrar): estatísticas em `UCard`, fonte citada.
- Seção 6 (Economia): dois `UCard` em `UGrid`.
- Seção 7 (Integrações): `UList` com ícones/nomes de plataformas.
- Seção 8 (Entrega): checklist com `UList` e ícones de check.
- Seção 9 (CTA final): `UHeading` + `UButton`.

## Fases de Execução
1. Instalar Nuxt e Nuxt UI.
2. Criar layout e `pages/index.vue`.
3. Implementar Seção 1 (Hero) conforme copy.
4. Implementar Seções 2–9 como componentes, consumindo `content/copy.ts`.
5. SEO e metadados com `useHead`.
6. Testes visuais/responsivos; ajustes usando props dos componentes Nuxt UI.

## Validação
- Rodar `npm run dev` e revisar no navegador.
- Conferir fidelidade da copy, responsividade e CTAs.

## Observações
- 100% Nuxt UI: evitar CSS custom; usar apenas componentes e props.
- CTA "Agendar reunião" aponta para URL externa; modal com formulário pode ser adicionado em fase posterior se desejado.