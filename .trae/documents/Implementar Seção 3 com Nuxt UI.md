## Objetivo
- Implementar a "# SEÇAO 3" (O cenário atual) usando componentes Nuxt UI, mantendo paleta primária lime, neutral zinc e fundo padrão `#171717`.

## Conteúdo da Seção
- Título: "O cenário atual"
- Subtítulo: "Sem IA, uma associação precisa de 4 pessoas para atender 200 leads."
- Texto: "Com IA, 2 pessoas fazem o mesmo trabalho — em menos tempo e com mais resultado."
- Itens (lista):
  - Tempo médio de fechamento: cai de 7 para 2 dias
  - Taxa de conversão: sobe de 30% para 45%
  - Economia média: até R$ 100 mil/ano em custos operacionais

## Componentes Nuxt UI
- `UPageSection` para a seção responsiva (props: `title`, `description`).
- `UPageList` para listar os indicadores em coluna.
- Opcional: `UPageColumns` se quisermos dividir texto explicativo e lista em duas colunas em telas maiores.

## Layout e Estilo
- Fundo: `class="bg-default"` no container da seção.
- Título: `text-highlighted`, subtítulo: `text-muted` (tokens Nuxt UI).
- Lista: itens com `text-default`, ícones/bolinhas padrão.
- Espaçamento padrão de seção: `py-16 sm:py-24 lg:py-32`.

## Passos de Implementação
1. Adicionar dados da Seção 3 em `content/copy.ts`:
   - `section3 = { title, subtitle, text, items: [...] }`.
2. Criar `components/SectionScenario.vue`:
   - `UPageSection` com `:title`, `:description`.
   - Slot `default` contendo `UPageList` com `<li>` para cada item da lista.
   - Classe `bg-default` para fundo.
3. Incluir `<SectionScenario />` após a Seção 2 em `pages/index.vue`.
4. Validação visual:
   - Conferir no preview que fundo está `#171717`, tipografia e espaciamentos corretos.
   - Confirmar que os itens aparecem como lista vertical empilhada.

## Entregáveis
- Novo componente `components/SectionScenario.vue`.
- Atualização de `content/copy.ts` com dados da seção 3.
- Inclusão em `pages/index.vue`.

Confirma execução do plano?