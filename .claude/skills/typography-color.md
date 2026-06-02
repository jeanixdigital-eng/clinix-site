# Skill: Typography & Color — Harmonia Visual Profissional

Regras que typographers e brand designers usam em projetos de alto padrão.
Aplicar sempre que editar fontes, tamanhos ou cores no CLINIX_SITE.

## Tipografia Profissional

### Escala tipográfica (proporção áurea 1.25)
```
Display:  clamp(52px, 7vw, 88px)   — apenas hero headlines
H1:       clamp(38px, 5vw, 64px)   — uma por página
H2:       clamp(28px, 4vw, 48px)   — títulos de seção
H3:       clamp(20px, 2.5vw, 28px) — subtítulos
Body L:   clamp(17px, 1.5vw, 20px) — parágrafos principais
Body:     clamp(15px, 1.2vw, 17px) — texto padrão
Small:    clamp(12px, 1vw, 14px)   — labels, captions
Micro:    clamp(10px, 0.8vw, 12px) — badges, tags
```

### Combinações de fonte do CLINIX_SITE
- **Syne 800** + letter-spacing -0.03em = headlines de impacto máximo
- **Playfair Display italic** = citações, frases de destaque, elementos poéticos
- **DM Sans 300/400** = corpo de texto longo (alta legibilidade)
- **DM Sans 600** = labels uppercase com letter-spacing 0.15em

### Regras absolutas de tipografia
- Nunca misturar mais de 2 famílias de fonte em uma seção
- Line-height para corpo: 1.65–1.75 (respiração confortável)
- Line-height para títulos: 1.05–1.15 (compacto = premium)
- Max-width de parágrafos: 65ch (65 caracteres)
- Letter-spacing uppercase labels: 0.1em–0.2em

### O que evitar
- ❌ Font-size abaixo de 14px em qualquer device
- ❌ Mais de 3 pesos de fonte na mesma seção
- ❌ Texto centralizado em parágrafos longos (difícil de ler)
- ❌ Letter-spacing negativo em textos pequenos

---

## Teoria das Cores — Aplicada ao CLINIX_SITE

### Paleta atual e seus papéis
```
--night  #050C1A  → fundo máximo (seções hero, CTA)
--deep   #070D1F  → fundo padrão (maioria das seções)
--card   #0D1530  → superfície elevada (cards, modais)
--royal  #1A2E8A  → azul profundo (bordas, backgrounds de destaque)
--electric #2A4DB5 → azul médio (gradientes, botão secundário)
--glow   #3D6FE8  → azul vivo (hovers, glows)
--bright #4A7FFF  → azul destaque PRINCIPAL (CTAs, links ativos)
--muted  #6B7FA3  → texto secundário, placeholders
--ice    #B8CCF0  → texto claro em fundos escuros
--soft   #E8EEFF  → texto principal em fundos escuros
--white  #FFFFFF  → texto máximo, títulos em dark backgrounds
```

### Como usar as cores corretamente
- **1 cor de ação** — apenas `--bright` para CTAs e elementos interativos
- **Profundidade** — use `--night` → `--deep` → `--card` para criar camadas
- **Texto em dark background**: `--white` para H1, `--soft` para corpo, `--ice` para secundário, `--muted` para terciário
- **Bordas**: `rgba(74,127,255,0.1)` padrão → `rgba(74,127,255,0.3)` no hover

### Gradientes premium
```css
/* Texto gradiente (headlines) */
background: linear-gradient(135deg, #4A7FFF 0%, #B8CCF0 100%);

/* Background de destaque sutil */
background: linear-gradient(135deg, rgba(74,127,255,0.08), rgba(42,77,181,0.06));

/* Glow sutil (cards featured) */
background: radial-gradient(ellipse at top right, rgba(74,127,255,0.12), transparent 70%);

/* Separador de seção */
background: linear-gradient(90deg, transparent, rgba(74,127,255,0.3), transparent);
```

### Contraste mínimo obrigatório (WCAG AA)
- Texto normal em fundo escuro: mínimo 4.5:1
- `--soft` (#E8EEFF) sobre `--deep` (#070D1F): ✅ passa
- `--muted` (#6B7FA3) sobre `--deep` (#070D1F): ✅ passa (3.1:1 — apenas para texto grande)
- Nunca usar `--muted` para texto de corpo em tamanho normal
