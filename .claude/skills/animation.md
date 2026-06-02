# Skill: Animações Profissionais (GSAP + CSS)

Ao criar ou editar animações no CLINIX_SITE, siga estas regras:

## Princípios
- Micro-interações: 150–300ms com `ease-out` ou spring
- Animações de entrada: 400–700ms com `cubic-bezier(0.16, 1, 0.3, 1)` (spring suave)
- Scroll reveals: usar `gsap.from()` com `ScrollTrigger` — nunca `display:none`
- Sempre incluir `prefers-reduced-motion`: desativar animações para usuários sensíveis
- Nunca usar `transform` e `position` ao mesmo tempo (causa reflow)
- Preferir `transform` e `opacity` (GPU-accelerated, sem layout shift)

## Padrão de Scroll Reveal (GSAP)
```javascript
gsap.registerPlugin(ScrollTrigger);

// Reveal suave para elementos com classe .reveal
gsap.utils.toArray('.reveal').forEach(el => {
  gsap.from(el, {
    opacity: 0,
    y: 40,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: {
      trigger: el,
      start: 'top 85%',
      once: true
    }
  });
});
```

## Padrão de Hover (CSS — sem JS)
```css
.btn { transition: transform 0.2s cubic-bezier(0.34, 1.56, 0.64, 1), box-shadow 0.2s ease; }
.btn:hover { transform: translateY(-2px); }
.btn:active { transform: translateY(0); transition-duration: 0.1s; }
```

## Stagger (elementos em sequência)
```javascript
gsap.from('.card', {
  opacity: 0, y: 30, duration: 0.6,
  stagger: 0.1, ease: 'power2.out',
  scrollTrigger: { trigger: '.cards-container', start: 'top 80%', once: true }
});
```

## Smooth Scroll (Lenis)
```javascript
const lenis = new Lenis({ duration: 1.2, easing: t => Math.min(1, 1.001 - Math.pow(2, -10 * t)) });
function raf(time) { lenis.raf(time); requestAnimationFrame(raf); }
requestAnimationFrame(raf);
// Integrar com GSAP ScrollTrigger:
lenis.on('scroll', ScrollTrigger.update);
gsap.ticker.add(time => lenis.raf(time * 1000));
```

## prefers-reduced-motion (obrigatório)
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
}
```
