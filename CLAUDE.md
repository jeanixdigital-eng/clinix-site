# CLINIX_SITE — Contexto e Padrões do Projeto

## O que é
Landing page do **Clinix System** — SaaS de operação inteligente para clínicas odontológicas.
Objetivo: converter visitantes em leads qualificados via anúncios (Meta, TikTok, Google).

## Estrutura
- **Arquivo único:** `index.html` (HTML + CSS inline + JavaScript inline)
- **Preview ao vivo:** Live Server na porta `http://127.0.0.1:5500`
- **NUNCA alterar textos/copy** — apenas estilos (CSS, fontes, cores, animações, layout)

---

## Paleta de Cores Atual
```css
--night: #050C1A   /* fundo mais escuro */
--deep:  #070D1F   /* fundo base */
--royal: #1A2E8A
--electric: #2A4DB5
--glow:  #3D6FE8
--bright: #4A7FFF  /* cor de destaque principal */
--ice:   #B8CCF0   /* texto secundário claro */
--white: #FFFFFF
--soft:  #E8EEFF   /* texto suave */
--muted: #6B7FA3   /* texto apagado */
--card:  #0D1530   /* fundo dos cards */
```

## Fontes Atuais
- **Syne** (400/600/700/800) — títulos e headlines
- **Playfair Display** (serif, itálico) — frases de destaque e citações
- **Inter** (400/500/600) — corpo do texto (projetada para telas, peso mínimo 400)

## Seções do Site
1. Hero — headline principal + CTA
2. Diagnóstico — estatísticas e gráfico de conversão
3. Virada — tabela comparativa antes/depois
4. Sistema — 5 componentes do produto
5. Funil — jornada completa do lead (acordeão)
6. Ciência — pilares comportamentais + timeline
7. Investimento — calculadora de ROI + preços
8. CTA final + Footer

---

## PADRÕES TÉCNICOS OBRIGATÓRIOS

### SEO Técnico (Google)
- `<title>` único, 50–60 caracteres, palavra-chave principal no início
- `<meta name="description">` 120–160 caracteres, CTA implícito
- Open Graph completo: `og:title`, `og:description`, `og:image` (1200×630px), `og:url`, `og:type`
- Twitter Card: `twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`
- JSON-LD Schema.org: tipo `MedicalBusiness` ou `SoftwareApplication` + `WebPage`
- `<html lang="pt-BR">` sempre presente
- URL canônica: `<link rel="canonical" href="...">`
- Hierarquia de headings: apenas 1 `<h1>` por página, `<h2>` para seções, `<h3>` para subseções
- Todas as imagens com `alt` descritivo, `width`, `height` e `loading="lazy"`
- Imagens em formato WebP quando possível

### Performance (Core Web Vitals)
**Metas obrigatórias:**
- Lighthouse Performance ≥ 90
- Lighthouse SEO ≥ 95
- Lighthouse Accessibility = 100
- LCP ≤ 2.5s | INP ≤ 200ms | CLS ≤ 0.1

**Regras:**
- Fontes com `font-display: swap` para evitar FOIT
- CSS crítico (above the fold) inline no `<head>`
- Scripts não-críticos com `defer` ou `async`
- Imagens com dimensões explícitas (evita CLS)
- Preconnect para domínios de fontes: `<link rel="preconnect" href="https://fonts.googleapis.com">`
- Preload para recurso mais importante: `<link rel="preload" as="font">`

### Acessibilidade (WCAG 2.1 AA)
- Contraste mínimo 4.5:1 para texto normal, 3:1 para texto grande
- Todos os botões e links com texto descritivo ou `aria-label`
- Formulários com `<label>` associado via `for` + `id`
- Foco visível em todos os elementos interativos
- `role` e `aria-*` onde necessário para leitores de tela

### Rastreamento (Meta, TikTok, Google)
**Estrutura obrigatória do `<head>` (ordem importa):**
```html
<!-- 1. dataLayer antes de tudo -->
<script>window.dataLayer = window.dataLayer || [];</script>

<!-- 2. Captura de UTMs (antes do GTM) -->
<script>
(function() {
  var params = new URLSearchParams(window.location.search);
  var utms = ['utm_source','utm_medium','utm_campaign','utm_content','utm_term','fbclid','ttclid','gclid'];
  utms.forEach(function(k) {
    var v = params.get(k);
    if (v) {
      sessionStorage.setItem(k, v);
      dataLayer.push({[k]: v});
    }
  });
  dataLayer.push({event: 'page_view', page_type: 'landing'});
})();
</script>

<!-- 3. Google Tag Manager (substitua GTM-XXXXXXX pelo ID real) -->
<!-- GTM gerencia: GA4, Meta Pixel, TikTok Pixel, conversões -->

<!-- 4. Meta Pixel (se não usar GTM) -->
<!-- 5. TikTok Pixel (se não usar GTM) -->
```

**Campos ocultos obrigatórios em qualquer formulário:**
```html
<input type="hidden" name="utm_source"   id="h_utm_source">
<input type="hidden" name="utm_medium"   id="h_utm_medium">
<input type="hidden" name="utm_campaign" id="h_utm_campaign">
<input type="hidden" name="utm_content"  id="h_utm_content">
<input type="hidden" name="fbclid"       id="h_fbclid">
```

**Script para popular campos ocultos no submit:**
```javascript
document.querySelector('form').addEventListener('submit', function() {
  ['utm_source','utm_medium','utm_campaign','utm_content','fbclid'].forEach(function(k) {
    var el = document.getElementById('h_' + k);
    if (el) el.value = sessionStorage.getItem(k) || '';
  });
});
```

### Estrutura de Arquivos
```
CLINIX_SITE/
├── index.html                  ← arquivo principal
├── CLAUDE.md                   ← contexto do projeto
├── sitemap.xml                 ← para indexação Google
├── robots.txt                  ← controle de crawlers
├── assets/
│   ├── logo/
│   │   ├── logo.svg            ← logo principal (vetorial)
│   │   ├── logo-white.svg      ← versão branca para dark backgrounds
│   │   └── favicon.png         ← ícone da aba (32x32px)
│   ├── images/
│   │   └── og-image.jpg        ← 1200×630px para redes sociais
│   └── icons/                  ← ícones adicionais
└── .claude/
    └── skills/                 ← habilidades do Claude para este projeto
```

---

## Fluxo de Rastreamento Profissional
```
Anúncio (Meta/TikTok/Google Ads)
  → UTM + fbclid/ttclid na URL
    → Landing page captura → sessionStorage + dataLayer
      → GTM dispara:
          ├── GA4 — analytics completo
          ├── Meta Pixel + CAPI — leads qualificados
          └── TikTok Pixel — conversões
      → Form submit: UTMs vão para o CRM
```

---

## Stack de Bibliotecas (CDN — sem npm/build)

```html
<!-- Smooth Scroll -->
<script src="https://cdn.jsdelivr.net/npm/@studio-freight/lenis@1.0.42/dist/lenis.min.js"></script>

<!-- GSAP + ScrollTrigger (animações profissionais) -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

<!-- ApexCharts (gráficos interativos) -->
<script src="https://cdn.jsdelivr.net/npm/apexcharts@latest/dist/apexcharts.min.js"></script>
```

**Quando usar cada um:**
- **Lenis** — sempre (smooth scroll em todo o site)
- **GSAP + ScrollTrigger** — reveals, parallax, animações complexas
- **ApexCharts** — substituir/melhorar o gráfico de barras da seção Diagnóstico
- **Three.js** — adicionar apenas se precisar de efeito 3D/WebGL (optional)

## Skills do Projeto (em `.claude/skills/`)
- `animation.md` — padrões GSAP, CSS transitions, prefers-reduced-motion
- `responsive.md` — mobile-first, clamp(), breakpoints, touch targets
- `ui-components.md` — glassmorphism, cards, botões, contadores, gráficos

## MCP Instalado
- **Playwright MCP** — usar para testar responsive em 375px, 768px, 1280px e tirar screenshots

## Checklist antes de publicar
- [ ] Lighthouse Performance ≥ 90
- [ ] Lighthouse SEO ≥ 95
- [ ] Meta Pixel Helper mostra eventos corretos
- [ ] TikTok Pixel Helper mostra eventos corretos
- [ ] UTMs chegam no GA4 DebugView
- [ ] og:image aparece corretamente no Sharing Debugger do Facebook
- [ ] Site responsivo em mobile (375px, 768px, 1280px)
- [ ] Nenhum erro no console do navegador
