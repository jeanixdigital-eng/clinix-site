# Skill: Componentes UI de Alto Padrão

Padrões de componentes para o CLINIX_SITE. Sempre usar estes padrões ao criar/editar UI.

## Glassmorphism (usado no nav e cards premium)
```css
.glass {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.08);
}
```

## Gradiente de texto (headlines premium)
```css
.gradient-text {
  background: linear-gradient(135deg, #4A7FFF 0%, #B8CCF0 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

## Botão com shimmer animado
```css
.btn-primary {
  position: relative;
  overflow: hidden;
}
.btn-primary::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
  transform: translateX(-100%);
  transition: transform 0.5s ease;
}
.btn-primary:hover::after { transform: translateX(100%); }
```

## Card com borda animada no hover
```css
.card {
  position: relative;
  background: var(--card);
  border: 1px solid rgba(74,127,255,0.1);
  border-radius: 20px;
  transition: border-color 0.3s, transform 0.3s, box-shadow 0.3s;
}
.card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--bright), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}
.card:hover { border-color: rgba(74,127,255,0.3); transform: translateY(-4px); box-shadow: 0 20px 48px rgba(0,0,0,0.4); }
.card:hover::before { opacity: 1; }
```

## Contador animado (números que sobem)
```javascript
function animateCounter(el, target, duration = 2000) {
  let start = 0;
  const step = timestamp => {
    if (!start) start = timestamp;
    const progress = Math.min((timestamp - start) / duration, 1);
    const ease = 1 - Math.pow(1 - progress, 3); // ease-out cubic
    el.textContent = Math.floor(ease * target).toLocaleString('pt-BR');
    if (progress < 1) requestAnimationFrame(step);
  };
  requestAnimationFrame(step);
}
```

## Gráfico de barras (ApexCharts)
```javascript
const options = {
  chart: { type: 'bar', background: 'transparent', toolbar: { show: false } },
  theme: { mode: 'dark' },
  colors: ['#4A7FFF'],
  plotOptions: { bar: { borderRadius: 6, horizontal: true } },
  dataLabels: { enabled: false },
  grid: { borderColor: 'rgba(255,255,255,0.06)' },
  xaxis: { labels: { style: { colors: '#6B7FA3' } } },
  yaxis: { labels: { style: { colors: '#6B7FA3' } } },
  series: [{ name: 'Valor', data: [] }]
};
```

## Partículas canvas (já existe no hero — padrão a manter)
- Manter o sistema de partículas atual no hero e CTA
- Pode adicionar em outras seções com `opacity` reduzida (0.3–0.5)
