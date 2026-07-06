# Components: Narrative Mode

Copy-paste HTML + CSS blocks for Narrative (scroll-snap slide) mode.
All examples use Dark-Glass palette — swap variables for your chosen palette.

---

## Slide Base Setup

Every narrative HTML must include:

```css
html { scroll-snap-type: y mandatory; scroll-behavior: smooth; height: 100%; }
body { height: 100%; overflow-x: hidden; }

.slide {
  width: 100vw; height: 100vh; height: 100dvh;
  scroll-snap-align: start;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  position: relative;
}
/* Slide number — bottom right */
.sn {
  position: absolute; bottom: 20px; right: 24px;
  font-family: var(--fm); font-size: 10px;
  color: var(--t3); letter-spacing: .1em;
}
```

---

## Navigation Dots

```html
<div class="nav-dots" id="nav-dots"></div>
```

```css
.nav-dots {
  position: fixed; right: 20px; top: 50%; transform: translateY(-50%);
  z-index: 100; display: flex; flex-direction: column; gap: 8px;
}
.nav-dot {
  width: 6px; height: 6px; border-radius: 50%;
  background: var(--bd); cursor: pointer;
  transition: all .3s; border: 1px solid transparent;
}
.nav-dot.on {
  background: var(--sl); transform: scale(1.5);
  border-color: rgba(122,154,184,.3);
}
```

```js
// Generate dots + track active slide
const slides = document.querySelectorAll('.slide');
const dotsEl  = document.getElementById('nav-dots');
slides.forEach((_, i) => {
  const d = document.createElement('div');
  d.className = 'nav-dot' + (i === 0 ? ' on' : '');
  d.onclick = () => slides[i].scrollIntoView({ behavior: 'smooth' });
  dotsEl.appendChild(d);
});
const dots = document.querySelectorAll('.nav-dot');
const obs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const idx = Array.from(slides).indexOf(e.target);
      dots.forEach((d, i) => d.classList.toggle('on', i === idx));
    }
  });
}, { threshold: 0.6 });
slides.forEach(s => obs.observe(s));
```

---

## Slide: Cover / Title

```html
<section class="slide slide-cover" id="sl0">
  <!-- Background layer: gradient or particle canvas -->
  <canvas id="cover-canvas" style="position:absolute;inset:0;width:100%;height:100%;pointer-events:none;"></canvas>

  <!-- Decorative rings (expressive motion only) -->
  <div class="deco-ring ring-1"></div>
  <div class="deco-ring ring-2"></div>

  <div class="slide-inner" style="position:relative;z-index:1;flex:1;display:flex;flex-direction:column;justify-content:center;padding:clamp(40px,6vw,80px);">
    <!-- Eyebrow label -->
    <div class="sl-ew reveal">
      <span class="sl-ew-line"></span>
      DATA REPORT · 2025
    </div>
    <!-- Main title -->
    <h1 class="sl-h1 reveal d1">
      核心洞察<br><span class="sl-h1-acc">标题关键词</span>
    </h1>
    <!-- Subtitle -->
    <p class="sl-sub reveal d2">报告描述 · 数据时间范围 · 来源</p>
    <!-- Data chips -->
    <div class="sl-chips reveal d3">
      <div class="chip"><span class="chip-n">14.3%</span><span class="chip-l">指标一</span></div>
      <div class="chip"><span class="chip-n">3,842</span><span class="chip-l">指标二</span></div>
      <div class="chip"><span class="chip-n">8</span><span class="chip-l">维度</span></div>
    </div>
  </div>

  <div class="sn">01 / 08</div>
</section>
```

```css
.sl-ew {
  font-family: var(--fm); font-size: 10px; letter-spacing: .18em;
  text-transform: uppercase; color: var(--t2);
  display: flex; align-items: center; gap: 12px; margin-bottom: 24px;
}
.sl-ew-line { width: 20px; height: 1px; background: var(--sl); }
.sl-h1 {
  font-size: clamp(2.4rem, 5vw, 5rem); font-weight: 800; line-height: 1.08;
  letter-spacing: -.025em; color: var(--t1); margin-bottom: 18px;
}
.sl-h1-acc { color: var(--sl); }
.sl-sub { font-size: 15px; color: var(--t2); margin-bottom: 36px; line-height: 1.6; }
.sl-chips { display: flex; gap: 12px; flex-wrap: wrap; }
.chip {
  display: flex; flex-direction: column; align-items: center;
  background: var(--glass); border: 1px solid var(--bd); border-radius: 12px;
  padding: 12px 20px; backdrop-filter: blur(12px);
}
.chip-n { font-family: var(--fm); font-size: 1.4rem; font-weight: 700; color: var(--t1); line-height: 1; }
.chip-l { font-family: var(--fm); font-size: 9px; color: var(--t2); margin-top: 5px; letter-spacing: .08em; text-transform: uppercase; }
```

---

## Slide: Key Metric (hero number)

```html
<section class="slide" id="sl2">
  <div class="slide-inner" style="flex:1;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:clamp(40px,6vw,80px);">
    <div class="sl-ew reveal" style="justify-content:center;">
      <span class="sl-ew-line"></span>CORE METRIC<span class="sl-ew-line"></span>
    </div>
    <div class="hero-num reveal d1">
      <span class="hero-val" data-count="14.3" data-suffix="%">0%</span>
    </div>
    <div class="hero-label reveal d2">核心指标名称</div>
    <p class="hero-ctx reveal d3">
      支撑数据说明，1-2句，解释这个数字的含义和背景。
    </p>
    <!-- 3 supporting mini-metrics -->
    <div class="hero-trio reveal d4">
      <div><span class="trio-n">+2.1pp</span><span class="trio-l">同比变化</span></div>
      <div class="trio-div"></div>
      <div><span class="trio-n">P0</span><span class="trio-l">优先级</span></div>
      <div class="trio-div"></div>
      <div><span class="trio-n">8类</span><span class="trio-l">覆盖维度</span></div>
    </div>
  </div>
  <div class="sn">03 / 08</div>
</section>
```

```css
.hero-num { margin: 12px 0 16px; }
.hero-val {
  font-family: var(--fm); font-size: clamp(4rem, 10vw, 8rem);
  font-weight: 700; color: var(--sl); line-height: 1; display: block;
}
.hero-label {
  font-size: 16px; font-weight: 700; color: var(--t1); margin-bottom: 14px;
}
.hero-ctx {
  font-size: 14px; color: var(--t2); line-height: 1.7;
  max-width: 480px; margin: 0 auto 32px;
}
.hero-trio {
  display: flex; align-items: center; gap: 0;
  background: var(--glass); border: 1px solid var(--bd); border-radius: 14px;
  padding: 14px 24px; backdrop-filter: blur(16px);
}
.hero-trio > div:not(.trio-div) { padding: 0 20px; display: flex; flex-direction: column; align-items: center; }
.trio-n { font-family: var(--fm); font-size: 1.3rem; font-weight: 700; color: var(--t1); }
.trio-l { font-family: var(--fm); font-size: 9px; color: var(--t2); margin-top: 4px; letter-spacing: .08em; text-transform: uppercase; }
.trio-div { width: 1px; height: 32px; background: var(--bd); }
```

---

## Slide: Chart Slide

```html
<section class="slide" id="sl3">
  <div class="sl-hdr reveal">
    <div class="sl-ew"><span class="sl-ew-line"></span>TREND ANALYSIS</div>
    <h2 class="sl-h2">趋势图标题</h2>
  </div>
  <div class="sl-chart-area reveal d1" style="flex:1;padding:0 clamp(32px,4vw,56px) 32px;">
    <div id="chart-slide" style="width:100%;height:100%;min-height:300px;max-height:65vh;"></div>
  </div>
  <!-- Footer insight strip -->
  <div class="sl-footer reveal d2">
    <div class="sl-fi">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="14" height="14"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
      <span>图表关键结论，一句话说清楚趋势方向和意义。</span>
    </div>
  </div>
  <div class="sn">04 / 08</div>
</section>
```

```css
.sl-hdr { padding: clamp(32px,4vw,56px) clamp(32px,4vw,56px) 20px; }
.sl-h2 { font-size: clamp(1.4rem, 2.5vw, 2rem); font-weight: 800; color: var(--t1); margin-top: 8px; letter-spacing: -.02em; }
.sl-footer {
  padding: 14px clamp(32px,4vw,56px);
  border-top: 1px solid var(--bd);
  background: var(--glass); backdrop-filter: blur(12px);
}
.sl-fi { display: flex; align-items: center; gap: 10px; font-size: 13px; color: var(--t2); }
.sl-fi svg { color: var(--sl); flex-shrink: 0; }
```

---

## Slide: Insight / Finding (text + 2-col split)

```html
<section class="slide" id="sl5">
  <div style="flex:1;display:flex;flex-direction:column;justify-content:center;padding:clamp(40px,5vw,72px);">
    <div class="sl-ew reveal"><span class="sl-ew-line"></span>KEY FINDING #1</div>
    <h2 class="sl-h2 reveal d1">洞察核心结论</h2>
    <p class="sl-body reveal d2">详细说明这个洞察的背景、数据证据、业务含义，2-3句话。</p>

    <!-- Evidence cards 2-col -->
    <div class="ev-grid reveal d3">
      <div class="ev-card">
        <div class="ev-num">64%</div>
        <div class="ev-label">数据依据一</div>
        <div class="ev-text">具体数字背后的说明</div>
      </div>
      <div class="ev-card">
        <div class="ev-num">3.2×</div>
        <div class="ev-label">数据依据二</div>
        <div class="ev-text">具体数字背后的说明</div>
      </div>
    </div>
  </div>
  <div class="sn">06 / 08</div>
</section>
```

```css
.sl-body { font-size: 15px; color: var(--t2); line-height: 1.75; max-width: 640px; margin: 12px 0 28px; }
.ev-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; max-width: 600px; }
.ev-card {
  background: var(--glass); border: 1px solid var(--bd); border-radius: 14px;
  padding: 20px 22px; backdrop-filter: blur(16px);
}
.ev-num { font-family: var(--fm); font-size: 2rem; font-weight: 700; color: var(--sl); margin-bottom: 6px; line-height: 1; }
.ev-label { font-family: var(--fm); font-size: 9px; text-transform: uppercase; letter-spacing: 1.5px; color: var(--t2); margin-bottom: 8px; }
.ev-text { font-size: 12.5px; color: var(--t2); line-height: 1.6; }
```

---

## Slide: Closing / CTA

```html
<section class="slide slide-end" id="slN">
  <div style="flex:1;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:clamp(40px,6vw,80px);">
    <div class="sl-ew reveal" style="justify-content:center;"><span class="sl-ew-line"></span>SUMMARY<span class="sl-ew-line"></span></div>
    <h2 class="sl-h2 reveal d1" style="text-align:center;max-width:560px;">核心结论与下一步</h2>
    <!-- Takeaway list -->
    <div class="takeaways reveal d2">
      <div class="tl">
        <div class="tl-n">01</div>
        <div class="tl-text">关键要点一：一句话陈述</div>
      </div>
      <div class="tl">
        <div class="tl-n">02</div>
        <div class="tl-text">关键要点二：一句话陈述</div>
      </div>
      <div class="tl">
        <div class="tl-n">03</div>
        <div class="tl-text">关键要点三：一句话陈述</div>
      </div>
    </div>
    <!-- Brand/source line -->
    <div class="end-brand reveal d3">Report Name · Generated by Claude · 2025</div>
  </div>
  <div class="sn">08 / 08</div>
</section>
```

```css
.takeaways { display: flex; flex-direction: column; gap: 12px; max-width: 520px; margin: 24px auto; text-align: left; }
.tl { display: flex; align-items: flex-start; gap: 16px; }
.tl-n { font-family: var(--fm); font-size: 11px; font-weight: 700; color: var(--sl); min-width: 24px; margin-top: 2px; }
.tl-text { font-size: 14px; color: var(--t1); line-height: 1.6; }
.end-brand { font-family: var(--fm); font-size: 10px; color: var(--t3); letter-spacing: .1em; margin-top: 32px; }
```

---

## Slide Scroll Reveal (Narrative)

In narrative mode, `.reveal` is triggered when a slide becomes active,
not on generic scroll. Use the slide IntersectionObserver:

```css
.reveal {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity .6s cubic-bezier(.16,1,.3,1), transform .6s cubic-bezier(.16,1,.3,1);
}
.reveal.revealed { opacity: 1; transform: none; }
.reveal.d1 { transition-delay: .1s; }
.reveal.d2 { transition-delay: .2s; }
.reveal.d3 { transition-delay: .3s; }
.reveal.d4 { transition-delay: .4s; }
```

```js
// Trigger reveals when a slide enters the viewport
const slideObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.reveal').forEach(el => el.classList.add('revealed'));
    }
  });
}, { threshold: 0.5 });
document.querySelectorAll('.slide').forEach(s => slideObs.observe(s));
```

---

## Editorial Narrative Variant (slate-warm palette)

For the `editorial` UI style in narrative mode, replace glass cards with
bordered left-bar components:

```css
/* Override chip style for editorial */
.chip {
  background: transparent;
  border: 1.5px solid var(--border);
  border-left: 3px solid var(--warm);
  border-radius: 0 var(--r) var(--r) 0;
  padding: 10px 16px;
}
/* Override ev-card for editorial */
.ev-card {
  background: var(--card);
  border: 1px solid var(--border-lt);
  border-left: 3px solid var(--primary);
  border-radius: 0 var(--r) var(--r) 0;
  backdrop-filter: none;
}
/* Large decorative pull-quote */
.pull-quote {
  font-family: var(--fh); font-size: clamp(1.8rem, 3.5vw, 3rem);
  font-weight: 700; font-style: italic; color: var(--text);
  line-height: 1.2; border-left: 4px solid var(--warm);
  padding-left: 24px; max-width: 600px;
}
.pull-attr { font-size: 13px; color: var(--muted); margin-top: 12px; font-style: normal; }
```
