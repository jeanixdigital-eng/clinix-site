# Skill: Design Director — Olho Visual Premium

Antes de escrever qualquer CSS, aplicar estes princípios de design de alto padrão.
Estes são os critérios que separam sites de agências premium de sites amadores.

## O que torna um site premium (Apple, Linear, Stripe)

### Espaço em branco (whitespace)
- Mais espaço é sempre melhor. Sites amadores têm medo do espaço vazio.
- Padding de seções: mínimo `clamp(80px, 12vw, 140px)`
- Entre elementos relacionados: 8px, 16px, 24px (escala de 8)
- Entre seções diferentes: 64px, 80px, 120px

### Hierarquia visual
- Máximo 3 tamanhos de fonte por seção
- O elemento mais importante deve ter contraste 3x maior que o secundário
- Um único ponto focal por seção — o olho do usuário precisa de um lugar para pousar

### Tipografia premium
- Line-height de títulos: 1.05–1.15 (muito compacto = sofisticado)
- Letter-spacing negativo em títulos grandes: `-0.02em` a `-0.04em`
- Nunca usar font-weight abaixo de 300 para corpo de texto
- Parágrafos: max-width 65–75 caracteres (medida ideal de leitura)

### Cores como profissional
- Paleta máxima: 2 cores de marca + neutros + 1 cor de acento
- Fundos: nunca preto puro (#000) — usar tons muito escuros (#050C1A)
- Gradientes premium: ângulo 135deg, 2–3 paradas, opacidade variável
- Bordas sutis: `rgba(255,255,255,0.06)` a `rgba(255,255,255,0.12)`

### O que NUNCA fazer (AI Slop — design genérico)
- ❌ Shadows muito óbvias (`box-shadow: 0 4px 6px rgba(0,0,0,0.1)`)
- ❌ Border-radius igual em tudo (variar: 8px, 16px, 20px, 100px)
- ❌ Gradientes de cor viva sem propósito (verde→azul aleatório)
- ❌ Ícones genéricos de emoji como decoração
- ❌ Cards todos iguais sem hierarquia de tamanho
- ❌ CTAs sem contraste suficiente com o fundo
- ❌ Animações que não têm propósito (movimento por movimento)

## Checklist visual antes de qualquer entrega
- [ ] Olhar a seção e perguntar: "isso parece R$ 50k ou R$ 5k?"
- [ ] Existe um único ponto focal claro?
- [ ] O espaçamento está generoso o suficiente?
- [ ] As fontes têm hierarquia clara (grande → médio → pequeno)?
- [ ] As cores têm contraste WCAG AA mínimo?
- [ ] Algum elemento parece "genérico de template"?

## Referências visuais a seguir
- **Apple.com** — espaço generoso, tipografia bold, fotografia como hero
- **Linear.app** — dark mode premium, gradientes sutis, micro-animações
- **Stripe.com** — clareza, hierarquia, CTAs impossíveis de ignorar
- **Vercel.com** — minimalismo extremo, cada pixel tem propósito
