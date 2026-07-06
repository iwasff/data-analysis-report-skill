# Animations Reference

Complete JavaScript patterns for all animation systems used across both modes.
Copy the relevant blocks verbatim — do not rewrite from memory.

---

## ⚠️ Critical: IntersectionObserver must observe Elements, not NodeLists

```js
// ✅ CORRECT — observe each element individually
document.querySelectorAll('.reveal').forEach(el => revObs.observe(el));
document.querySelectorAll('section[id]').forEach(s => navObs.observe(s));

// ❌ WRONG — NodeList throws TypeError: Failed to execute 'observe'
revObs.observe(document.querySelectorAll('.reveal'));
navObs.observe(document.querySelectorAll('section[id]'));
```

---

## Scroll Reveal (both modes)

```css
.reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity .55s ease, transform .55s ease;
}
.reveal.revealed { opacity: 1; transform: translateY(0); }
.reveal.d1 { transition-delay: .08s; }
.reveal.d2 { transition-delay: .16s; }
.reveal.d3 { transition-delay: .24s; }
.reveal.d4 { transition-delay: .32s; }
```

```js
const revObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('revealed');
  });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => revObs.observe(el));
```

---

## Sidebar Nav Active Tracking (analysis mode only)

Tracks which section is in viewport and highlights the matching sidebar link.

```js
const navObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      // Match section id → sidebar link href
      const lnk = document.querySelector(`.sb-link[href="#${e.target.id}"]`);
      if (lnk) {
        document.querySelectorAll('.sb-link').forEach(l => l.classList.remove('active'));
        lnk.classList.add('active');
      }
    }
  });
}, { threshold: 0.25 });

// Observe cover + all sections individually
document.querySelectorAll('.cover-sec, section[id]').forEach(s => navObs.observe(s));
```

**Sidebar smooth scroll** (click nav link → smooth scroll to section):
```js
document.querySelectorAll('.sb-link[href^="#"]').forEach(link => {
  link.addEventListener('click', e => {
    e.preventDefault();
    const target = document.querySelector(link.getAttribute('href'));
    if (target) target.scrollIntoView({ behavior: 'smooth' });
  });
});
```

---

## Counter Animation (standard + expressive motion)

Animates a number from 0 to its target value. Used on cover KPI chips.

```js
function animateCount(el, target, suffix = '', prefix = '') {
  const dur = 1800;
  const start = performance.now();
  const isDecimal = target % 1 !== 0;
  (function step(now) {
    const t    = Math.min((now - start) / dur, 1);
    const ease = 1 - Math.pow(1 - t, 3);  // ease-out-cubic
    const val  = isDecimal
      ? (target * ease).toFixed(1)
      : Math.round(target * ease);
    el.textContent = prefix + val + suffix;
    if (t < 1) requestAnimationFrame(step);
  })(start);
}
```

**HTML data attributes:**
```html
<span class="cvs-n" data-count="14.3" data-suffix="%" data-prefix="">0%</span>
<span class="cvs-n" data-count="3842" data-suffix="" data-prefix="">0</span>
```

**Bootstrap all counters on the page:**
```js
function runCounters() {
  document.querySelectorAll('[data-count]').forEach(el => {
    animateCount(
      el,
      parseFloat(el.dataset.count),
      el.dataset.suffix || '',
      el.dataset.prefix || ''
    );
  });
}
```

---

## Cover Replay on Scroll Return (analysis mode, standard + expressive)

Cover animations re-trigger every time the user scrolls back to the top.
Uses the `.playing` class pattern with a forced reflow to restart CSS animations.

```js
const coverEl = document.getElementById('cover');

function replayCover() {
  // Step 1: Remove playing class to reset
  coverEl.classList.remove('playing');
  // Step 2: Force browser reflow (so animation restart is detected)
  void coverEl.offsetWidth;
  // Step 3: Re-add playing to restart CSS animation
  coverEl.classList.add('playing');
  // Step 4: Delay counter start to sync with cover fade-in
  setTimeout(runCounters, 500);
}

// Observe cover visibility
new IntersectionObserver(entries => {
  if (entries[0].isIntersecting) replayCover();
}, { threshold: 0.05 }).observe(coverEl);

// Play immediately on page load
replayCover();
```

**Cover CSS:**
```css
#cover { opacity: 0; }
#cover.playing { animation: coverIn 1s cubic-bezier(.16,1,.3,1) forwards; }
@keyframes coverIn {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0);    }
}
```

---

## Narrative Slide Reveals (narrative mode)

Triggers `.reveal` elements when their parent slide enters the viewport.

```js
const slideObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      // Trigger all .reveal children in this slide
      e.target.querySelectorAll('.reveal').forEach(el => el.classList.add('revealed'));
    }
  });
}, { threshold: 0.5 });
document.querySelectorAll('.slide').forEach(s => slideObs.observe(s));
```

---

## Narrative Keyboard Navigation

```js
const slides = document.querySelectorAll('.slide');

document.addEventListener('keydown', e => {
  // Find currently-visible slide (top edge near 0)
  const idx = Array.from(slides).findIndex(s => {
    const r = s.getBoundingClientRect();
    return r.top >= -10 && r.top <= window.innerHeight * 0.1;
  });
  if (e.key === 'ArrowDown' || e.key === ' ') {
    e.preventDefault();
    if (idx < slides.length - 1) slides[idx + 1].scrollIntoView({ behavior: 'smooth' });
  }
  if (e.key === 'ArrowUp') {
    e.preventDefault();
    if (idx > 0) slides[idx - 1].scrollIntoView({ behavior: 'smooth' });
  }
});
```

---

## ECharts Resize Handler

Always add per chart — failure to do so causes layout breaks on window resize.

```js
// After initializing each chart:
const myChart = echarts.init(document.getElementById('chart-id'));
myChart.setOption({ /* ... */ });
window.addEventListener('resize', () => myChart.resize());
```

For multiple charts, collect and resize all:
```js
const charts = [];
// After each echarts.init():
charts.push(myChart);
// Single resize listener:
window.addEventListener('resize', () => charts.forEach(c => c.resize()));
```

---

## Stagger Entrance (expressive motion only)

```css
/* Parent gets .stagger; children animate sequentially */
.stagger > * {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity .6s cubic-bezier(.16,1,.3,1),
              transform .6s cubic-bezier(.16,1,.3,1);
}
.stagger.revealed > *:nth-child(1) { opacity:1; transform:none; transition-delay: .00s; }
.stagger.revealed > *:nth-child(2) { opacity:1; transform:none; transition-delay: .08s; }
.stagger.revealed > *:nth-child(3) { opacity:1; transform:none; transition-delay: .16s; }
.stagger.revealed > *:nth-child(4) { opacity:1; transform:none; transition-delay: .24s; }
.stagger.revealed > *:nth-child(5) { opacity:1; transform:none; transition-delay: .32s; }
.stagger.revealed > *:nth-child(6) { opacity:1; transform:none; transition-delay: .40s; }
```

```js
// Use same IntersectionObserver as scroll reveal — .stagger gets .revealed
const revObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('revealed');
  });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal, .stagger').forEach(el => revObs.observe(el));
```

---

## Particle System (expressive motion only)

```js
class ParticleSystem {
  constructor(canvas, opts = {}) {
    this.canvas = canvas;
    this.ctx    = canvas.getContext('2d');
    this.count  = opts.count || 60;
    this.color  = opts.color || 'rgba(208,152,106,0.2)';
    this.pts    = [];
    this.resize();
    for (let i = 0; i < this.count; i++) this.pts.push(this._new());
    window.addEventListener('resize', () => this.resize());
    this._loop();
  }
  resize() {
    this.canvas.width  = this.canvas.offsetWidth;
    this.canvas.height = this.canvas.offsetHeight;
  }
  _new() {
    return {
      x:  Math.random() * this.canvas.width,
      y:  Math.random() * this.canvas.height,
      vx: (Math.random() - .5) * .5,
      vy: (Math.random() - .5) * .5,
      r:  .5 + Math.random() * 2,
      o:  .05 + Math.random() * .18,
    };
  }
  _loop() {
    const { ctx, canvas } = this;
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    this.pts.forEach(p => {
      p.vx *= .99; p.vy *= .99;
      p.x  += p.vx; p.y += p.vy;
      if (p.x < 0 || p.x > canvas.width)  p.vx *= -1;
      if (p.y < 0 || p.y > canvas.height) p.vy *= -1;
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
      ctx.fillStyle = this.color;
      ctx.fill();
    });
    requestAnimationFrame(() => this._loop());
  }
}

// Usage:
const canvas = document.getElementById('cover-canvas');
if (canvas) new ParticleSystem(canvas, { count: 60, color: 'rgba(208,152,106,.18)' });
```

---

## Custom Cursor (expressive analysis mode)

```css
* { cursor: none; }
#cursor-dot {
  position: fixed; z-index: 9999; pointer-events: none;
  width: 6px; height: 6px; border-radius: 50%;
  background: var(--sd); transform: translate(-50%, -50%);
  transition: transform .08s;
}
#cursor-ring {
  position: fixed; z-index: 9998; pointer-events: none;
  width: 28px; height: 28px; border-radius: 50%;
  border: 1.5px solid var(--sd); opacity: .7;
  transform: translate(-50%, -50%);
  transition: left .12s cubic-bezier(.16,1,.3,1),
              top  .12s cubic-bezier(.16,1,.3,1);
}
```

```js
const dot  = document.getElementById('cursor-dot');
const ring = document.getElementById('cursor-ring');
if (dot && ring) {
  document.addEventListener('mousemove', e => {
    dot.style.left   = e.clientX + 'px';
    dot.style.top    = e.clientY + 'px';
    ring.style.left  = e.clientX + 'px';
    ring.style.top   = e.clientY + 'px';
  });
}
```

---

## Progress Bar (analysis mode, optional)

Thin line at the very top of the page showing scroll progress.

```html
<div id="pg-bar"></div>
```
```css
#pg-bar {
  position: fixed; top: 0; left: var(--nav); right: 0; height: 2px;
  background: rgba(163,177,138,.15); z-index: 300;
}
#pg-bar::after {
  content: ''; display: block; height: 100%;
  background: var(--sd);
  width: var(--prog, 0%);
  transition: width .1s;
}
```
```js
const pgBar = document.getElementById('pg-bar');
if (pgBar) {
  document.addEventListener('scroll', () => {
    const h = document.documentElement;
    const pct = (h.scrollTop / (h.scrollHeight - h.clientHeight)) * 100;
    pgBar.style.setProperty('--prog', pct + '%');
  });
}
```
