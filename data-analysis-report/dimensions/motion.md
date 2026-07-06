# Dimension: Motion

Three motion levels. Each level is a superset of the previous:
`subtle` ⊂ `standard` ⊂ `expressive`.

---

## subtle

**Character:** Scroll-triggered fade-in only. Content appears smoothly as the
user scrolls; no cover counters, no chart entrance animation.

**Use when:** Internal documents, content-heavy reports where distraction is unwanted,
performance-critical deployments.

### CSS

```css
/* ── Scroll Reveal ── */
.reveal {
  opacity: 0;
  transform: translateY(16px);
  transition: opacity .45s ease, transform .45s ease;
}
.reveal.revealed { opacity: 1; transform: translateY(0); }

/* Stagger delays */
.reveal.d1 { transition-delay: .06s; }
.reveal.d2 { transition-delay: .12s; }
.reveal.d3 { transition-delay: .18s; }
.reveal.d4 { transition-delay: .24s; }
```

### JS

```js
// Apply .reveal to every section element before this script runs
const revObs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('revealed'); });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => revObs.observe(el));
```

---

## standard (Default)

**Character:** Scroll reveal + ECharts entrance animation + cover counter animation.
The balanced default for production reports.

Includes everything in `subtle`, plus:
- KPI counter animation on cover (numbers count up on load/replay)
- ECharts series animation enabled (default duration 800ms)
- Cover re-animates every time user scrolls back to top

### CSS (adds to subtle)

```css
/* Cover entrance animation */
#cover { opacity: 0; }
#cover.playing { animation: coverIn 1s var(--e1) forwards; }
@keyframes coverIn { from { opacity:0; transform:translateY(20px); } to { opacity:1; transform:translateY(0); } }

/* Cover KPI values */
.cv-kpi-val {
  font-family: var(--fm);
  font-size: 2.2rem; font-weight: 700;
  line-height: 1; color: var(--sd);
  display: block;
}
```

### JS — Counter animation

```js
function animateCount(el, target, suffix = '', prefix = '') {
  const dur = 1800, start = performance.now(), isDecimal = target % 1 !== 0;
  (function step(now) {
    const t = Math.min((now - start) / dur, 1);
    const ease = 1 - Math.pow(1 - t, 3);  // ease-out-cubic
    el.textContent = prefix + (isDecimal ? (target * ease).toFixed(2) : Math.round(target * ease)) + suffix;
    if (t < 1) requestAnimationFrame(step);
  })(start);
}
```

### JS — Cover replay on scroll return

```js
const coverEl = document.getElementById('cover');

function replayCover() {
  coverEl.classList.remove('playing');
  void coverEl.offsetWidth;  // force reflow to reset animation
  coverEl.classList.add('playing');
  // Delay counter start to sync with cover fade-in
  setTimeout(() => {
    document.querySelectorAll('#cover [data-count]').forEach(el => {
      animateCount(el, parseFloat(el.dataset.count),
                   el.dataset.suffix || '', el.dataset.prefix || '');
    });
  }, 500);
}

// Cover replay observer
new IntersectionObserver(entries => {
  if (entries[0].isIntersecting) replayCover();
}, { threshold: 0.05 }).observe(coverEl);

// Play on initial load
replayCover();
```

**Cover KPI HTML pattern:**
```html
<span class="cv-kpi-val" data-count="14.3" data-suffix="%" data-prefix="">0%</span>
```

### ECharts animation settings (standard)

Enable default ECharts animation (it is on by default). For emphasis:
```js
// Per-series entrance delay for stagger effect
series: [
  { animation: true, animationDuration: 800, animationDelay: 0, ... },
  { animation: true, animationDuration: 800, animationDelay: 100, ... },
]
```

---

## expressive

**Character:** Full motion — particle backgrounds, stagger entrance, all chart
animations, rotating decorative elements, card hover depth effects.

**Use when:** Portfolio demos, external showcase, CamPulse-style brand reports.
**Trade-off:** Slower initial load; avoid for data-dense internal documents.

Includes everything in `standard`, plus:

### Particle background (canvas)

```js
class ParticleSystem {
  constructor(canvas, count = 60, color = 'rgba(208,152,106,0.25)') {
    this.canvas = canvas;
    this.ctx = canvas.getContext('2d');
    this.particles = [];
    this.color = color;
    this.resize();
    for (let i = 0; i < count; i++) this.particles.push(this.newParticle());
    window.addEventListener('resize', () => this.resize());
    this.animate();
  }
  resize() {
    this.canvas.width  = this.canvas.offsetWidth;
    this.canvas.height = this.canvas.offsetHeight;
  }
  newParticle() {
    return {
      x: Math.random() * this.canvas.width,
      y: Math.random() * this.canvas.height,
      vx: (Math.random() - 0.5) * 0.5,
      vy: (Math.random() - 0.5) * 0.5,
      r: 0.5 + Math.random() * 2,
      o: 0.05 + Math.random() * 0.2,
    };
  }
  animate() {
    const { ctx, canvas } = this;
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    this.particles.forEach(p => {
      p.vx *= 0.99; p.vy *= 0.99;
      p.x += p.vx; p.y += p.vy;
      if (p.x < 0 || p.x > canvas.width)  p.vx *= -1;
      if (p.y < 0 || p.y > canvas.height) p.vy *= -1;
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
      ctx.fillStyle = this.color;
      ctx.fill();
    });
    requestAnimationFrame(() => this.animate());
  }
}

// Usage: call after DOM is ready
const cvCanvas = document.getElementById('cover-canvas');
if (cvCanvas) new ParticleSystem(cvCanvas);
```

Cover HTML for particle canvas:
```html
<div id="cover" style="position:relative; overflow:hidden;">
  <canvas id="cover-canvas" style="position:absolute;inset:0;width:100%;height:100%;pointer-events:none;"></canvas>
  <div class="cover-content" style="position:relative;z-index:1;">
    <!-- cover content here -->
  </div>
</div>
```

### Stagger entrance (expressive variant)

```css
/* Tighter stagger for slide-in from below */
.stagger > * {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity .6s var(--e1), transform .6s var(--e1);
}
.stagger.revealed > *:nth-child(1) { opacity:1; transform:none; transition-delay: .0s; }
.stagger.revealed > *:nth-child(2) { opacity:1; transform:none; transition-delay: .08s; }
.stagger.revealed > *:nth-child(3) { opacity:1; transform:none; transition-delay: .16s; }
.stagger.revealed > *:nth-child(4) { opacity:1; transform:none; transition-delay: .24s; }
.stagger.revealed > *:nth-child(5) { opacity:1; transform:none; transition-delay: .32s; }
.stagger.revealed > *:nth-child(6) { opacity:1; transform:none; transition-delay: .40s; }
```

### Card hover depth (3D tilt)

```js
document.querySelectorAll('.card-3d').forEach(card => {
  card.style.transformStyle = 'preserve-3d';
  card.addEventListener('mousemove', e => {
    const r = card.getBoundingClientRect();
    const x = (e.clientX - r.left) / r.width  - 0.5;
    const y = (e.clientY - r.top)  / r.height - 0.5;
    card.style.transform = `perspective(600px) rotateY(${x * 6}deg) rotateX(${-y * 6}deg) translateY(-3px)`;
  });
  card.addEventListener('mouseleave', () => {
    card.style.transform = '';
  });
});
```

### Rotating decoration (cover / narrative cover)

```css
.deco-ring {
  position: absolute;
  border-radius: 50%;
  border: 1px solid;
  animation: spin-slow var(--spin-dur, 20s) linear infinite;
  pointer-events: none;
}
@keyframes spin-slow { to { transform: rotate(360deg); } }

/* Example usage */
.deco-ring-1 {
  width: 300px; height: 300px;
  border-color: rgba(208,152,106,.12);
  top: -80px; right: -80px;
  --spin-dur: 18s;
}
.deco-ring-2 {
  width: 180px; height: 180px;
  border-color: rgba(208,152,106,.08);
  bottom: -40px; right: 60px;
  --spin-dur: 28s;
  animation-direction: reverse;
}
```

### Custom cursor (expressive only)

```css
* { cursor: none; }
#cursor-dot {
  position: fixed; z-index: 9999; pointer-events: none;
  width: 6px; height: 6px; border-radius: 50%;
  background: var(--sd);
  transform: translate(-50%, -50%);
  transition: transform .1s;
}
#cursor-ring {
  position: fixed; z-index: 9998; pointer-events: none;
  width: 28px; height: 28px; border-radius: 50%;
  border: 1.5px solid var(--sd);
  transform: translate(-50%, -50%);
  transition: transform .15s var(--e1), width .2s, height .2s;
}
```

```js
const dot  = document.getElementById('cursor-dot');
const ring = document.getElementById('cursor-ring');
document.addEventListener('mousemove', e => {
  dot.style.left  = e.clientX + 'px';
  dot.style.top   = e.clientY + 'px';
  ring.style.left = e.clientX + 'px';
  ring.style.top  = e.clientY + 'px';
});
```

### ECharts animation settings (expressive)

```js
// Longer, more dramatic entrance
series: [{
  animation: true,
  animationDuration: 1200,
  animationEasing: 'elasticOut',
  animationDelay: idx => idx * 80,
}]
```
