## Objetivo
- Implementar a "# SEÇAO 2" do arquivo `docs/Copy-LP-KivoIA` usando componentes do Nuxt UI, mantendo a paleta atual (primária lime, neutral zinc) e fundo padrão `#171717`.

## Conteúdo
- Título: "Sua equipe perde tempo entre CRM, planilha, contrato, cobrança e sinistro?"
- Subtítulo: "A Kivo IA conecta tudo o que você já usa — WhatsApp, redes sociais e sistemas de gestão — com automações que vendem, cobram e atendem de forma inteligente."

## Componentes Nuxt UI
- `UPageSection` para a seção responsiva (props: `title`, `description`, `links`).
- `UContainer` é opcional se quisermos controle extra de largura, mas `UPageSection` já renderiza com grid/tipografia adequadas.
- Botão opcional: `UButton` em `links` (CTA secundário) alinhado com a paleta.

## Layout e Estilo
- Fundo: usar `class="bg-default"` no `UPageSection` (amarrado ao `--ui-bg` que já está `#171717`).
- Texto: `text-default` para corpo, `text-highlighted` para título (Nuxt UI tokens).
- Espaçamento: aproveitar padding padrão do `UPageSection` (`py-24 sm:py-32 lg:py-40`).
- Radius: mantido pelo `--ui-radius: 0.125rem` já definido.

## Passos de Implementação
1. Adicionar as strings da SEÇAO 2 em `content/copy.ts` seguindo o padrão da seção hero:
   - `section2 = { title, subtitle }`.
2. Criar `components/SectionProblem.vue` com `UPageSection`:
   - `:title="copy.section2.title"`
   - `:description="copy.section2.subtitle"`
   - `class="bg-default"`
   - Opcional: `:links="[{ label: 'Saiba mais', to: '#apresentacao', color: 'neutral', variant: 'outline' }]"`
3. Incluir `<SectionProblem />` abaixo do `<SectionHero />` em `pages/index.vue`.
4. Garantir a paleta:
   - `app.config.ts` com `ui.colors = { primary: 'lime', neutral: 'zinc' }` (já configurado).
   - Fundo padrão via `assets/css/main.css`: `--ui-bg: #171717` (já configurado).
5. Validar no preview local que:
   - Fundo da seção aparece `#171717`.
   - Título e subtítulo usam neutral zinc (brancos/cinza) e CTA secundário em neutral outline.

## Notas Técnicas
- `UPageSection` aceita `title`, `description` e `links` (metadados confirmados). 
- Usar classes Nuxt UI (`bg-default`, `text-default`, `text-highlighted`) para aderir ao sistema de tokens.

## Entregáveis
- Novo componente `components/SectionProblem.vue`.
- Atualização de `content/copy.ts` com dados da seção 2.
- Inclusão em `pages/index.vue`.

Confirma a execução do plano?