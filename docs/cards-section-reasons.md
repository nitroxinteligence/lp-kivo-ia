# Características dos Cards - Seção "Por que as empresas estão migrando para IA"

## Estrutura Geral

**Componente:** `SectionReasons.vue`
**Localização:** `/components/SectionReasons.vue`
**Framework:** Nuxt UI + Vue 3 Composition API

## Layout

### Grid
- **Desktop (≥768px):** 3 colunas (`md:grid-cols-3`)
- **Mobile:** 1 coluna (`grid-cols-1`)
- **Gap:** `gap-6` (1.5rem / 24px)
- **Max Width:** `max-w-7xl` (80rem / 1280px)
- **Margin:** `mx-auto` (centralizado)

## Componentes

### UCard (Nuxt UI)
**Variant:** `subtle`
**Classes customizadas:**
```css
group hover:ring-primary/50 transition-all duration-300 !border !border-[#27272A]
```

## Cores

### Bordas
- **Padrão:** `#27272A` (cinza escuro)
- **Hover Ring:** `primary/50` (cor primary com 50% opacidade)

### Background
- **Card:** Definido pelo variant `subtle` do Nuxt UI
- **Ícone Container:** `bg-primary/10` (10% opacidade)
- **Ícone Container Hover:** `bg-primary/20` (20% opacidade)

### Texto
- **Porcentagem:** `text-primary` (cor primary do tema)
- **Descrição:** `text-default` (cor de texto padrão do tema)

### Ícones
- **Cor:** `text-primary`
- **Tamanho:** `w-8 h-8` (2rem / 32px)

## Tamanhos e Espaçamentos

### Card
- **Padding interno:** `p-4` (1rem / 16px) no container do conteúdo
- **Border Radius:** Definido pelo Nuxt UI Card
- **Border Width:** `border` (1px)

### Container de Ícone
- **Tamanho:** `w-16 h-16` (4rem / 64px)
- **Border Radius:** `rounded-full` (círculo perfeito)
- **Display:** `flex items-center justify-center`

### Tipografia

#### Título da Seção
- **Tamanho:**
  - Mobile: `text-3xl` (30px)
  - Tablet: `sm:text-4xl` (36px)
  - Desktop: `lg:text-5xl` (48px)
- **Peso:** `font-bold` (700)
- **Tracking:** `tracking-tight` (-0.025em)
- **Cor:** `text-highlighted`
- **Line Height:** `leading-[48px]`
- **Alinhamento:** `text-center`
- **Text Balance:** `text-pretty`

#### Porcentagem
- **Tamanho:**
  - Base: `text-5xl` (48px)
  - SM: `sm:text-6xl` (60px)
- **Peso:** `font-bold` (700)
- **Cor:** `text-primary`

#### Descrição
- **Tamanho:**
  - Base: `text-sm` (14px)
  - SM: `sm:text-base` (16px)
- **Peso:** `font-medium` (500)
- **Cor:** `text-default`
- **Line Height:** `leading-relaxed` (1.625)

## Efeitos e Transições

### Hover Effects
- **Card:** `hover:ring-primary/50` - Adiciona um anel primary com 50% opacidade
- **Ícone Container:** `group-hover:bg-primary/20` - Aumenta opacidade de fundo de 10% para 20%
- **Transição:** `transition-all duration-300` (300ms)
- **Timing:** `ease` (padrão)

### Animação de Contador
- **Trigger:** Intersection Observer (threshold: 0.3)
- **Duração:** 2000ms (2 segundos)
- **Steps:** 60 passos
- **Incremento:** Progressivo até valor final
- **Easing:** Linear

## Ícones Utilizados

1. **Trending Up:** `i-lucide-trending-up` - 40%
2. **Piggy Bank:** `i-lucide-piggy-bank` - 35%
3. **Zap:** `i-lucide-zap` - 70%

## Estados dos Cards

### Normal
- Borda: `#27272A`
- Fundo do ícone: `primary/10`
- Sem ring

### Hover
- Ring: `primary/50`
- Fundo do ícone: `primary/20`
- Transição suave (300ms)

### Loading/Animating
- Contador animado de 0 até valor final
- Duração: 2 segundos
- Ativa quando seção entra no viewport (30% visível)

## Responsividade

### Mobile (< 768px)
- 1 coluna
- Cards empilhados verticalmente
- Gap de 6 (24px) entre cards
- Texto 5xl para porcentagem
- Texto sm para descrição

### Tablet/Desktop (≥ 768px)
- 3 colunas
- Cards lado a lado
- Gap de 6 (24px) entre cards
- Texto 6xl para porcentagem
- Texto base para descrição

## Badge de Fonte

**Localização:** Abaixo dos cards
**Classes:**
```css
!bg-transparent
!border-[#383838]
!text-[#a8a8a8]
!ring-[#383838]
!rounded-[10px]
[&>svg]:!text-[#a8a8a8]
```

**Propriedades:**
- Ícone: `i-lucide-globe`
- Variant: `outline`
- Color: `neutral`
- Size: `md`
- Border: `#383838`
- Texto: `#a8a8a8`
- Border Radius: `10px`

## Dados dos Cards

```javascript
const stats = [
  {
    icon: 'i-lucide-trending-up',
    value: 40,
    description: '7 em cada 10 empresas que adotaram automação comercial aumentaram as vendas em até 40%'
  },
  {
    icon: 'i-lucide-piggy-bank',
    value: 35,
    description: 'Atendimentos digitais com IA reduziram o custo por cliente em até 35%'
  },
  {
    icon: 'i-lucide-zap',
    value: 70,
    description: 'O tempo de resposta ao sinistro caiu até 70% em operações automatizadas'
  }
]
```

## Acessibilidade

- Uso de componentes semânticos do Nuxt UI
- Contraste adequado entre texto e fundo
- Ícones decorativos (não requerem alt text)
- Transições suaves para melhor UX
- Animação respeitando preferências de movimento reduzido (se configurado)

## Dependências

- **Nuxt UI:** `UCard`, `UContainer`, `UPageSection`, `UIcon`, `UBadge`
- **Vue 3:** Composition API (ref, computed, onMounted)
- **Intersection Observer API:** Para trigger da animação
- **Lucide Icons:** Via Nuxt Icon

## Notas de Implementação

1. A animação de contador só executa uma vez (observer é desconectado após primeira visualização)
2. O grupo (`group`) permite que o hover do card afete o container do ícone
3. O uso de `!` em classes força override de estilos do Nuxt UI
4. A cor `#27272A` é consistente com outros elementos do site
5. O variant `subtle` do UCard fornece um background sutil sem comprometer a visibilidade
