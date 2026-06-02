# Skill: Responsive Design Profissional

Ao criar layouts no CLINIX_SITE, seguir estas regras mobile-first:

## Breakpoints Padrão
```css
/* Mobile first — estilos base são para mobile */
/* sm  */ @media (min-width: 640px)  { }
/* md  */ @media (min-width: 768px)  { }
/* lg  */ @media (min-width: 1024px) { }
/* xl  */ @media (min-width: 1280px) { }
```

## Typography Fluida (sem media queries)
```css
/* Nunca usar px fixo para fontes — sempre clamp() */
.hero-headline { font-size: clamp(2rem, 6vw, 4.5rem); }
.section-title  { font-size: clamp(1.75rem, 4vw, 3.25rem); }
.body-text      { font-size: clamp(1rem, 1.5vw, 1.125rem); }
.section-label  { font-size: clamp(0.625rem, 1vw, 0.75rem); }
```

## Espaçamento Fluido
```css
.section-pad { padding: clamp(60px, 10vw, 120px) 0; }
.container   { padding: 0 clamp(20px, 5vw, 60px); max-width: 1100px; margin: 0 auto; }
```

## Grid Responsivo (CSS Grid auto-fit)
```css
/* Adapta automaticamente sem media query */
.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: clamp(16px, 3vw, 24px);
}
```

## Telas para testar (com Playwright MCP)
- 375px — iPhone SE / menor mobile
- 390px — iPhone 14 Pro
- 768px — iPad / tablet
- 1024px — laptop pequeno
- 1280px — desktop padrão
- 1440px — desktop grande

## Imagens Responsivas
```html
<img
  src="imagem.webp"
  alt="Descrição"
  width="800" height="450"
  loading="lazy"
  style="width:100%; height:auto;"
>
```

## Touch targets (mobile)
- Botões e links: mínimo 44×44px de área de toque
- Espaçamento entre links: mínimo 8px
- Inputs: mínimo 48px de altura

## Navegação Mobile
- Menu hamburger para telas < 768px
- Sticky header com `backdrop-filter: blur()`
- Evitar hover-only interactions (touch não tem hover)
