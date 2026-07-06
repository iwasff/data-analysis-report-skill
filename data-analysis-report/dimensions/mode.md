# Dimension: Mode

Determines the overall layout paradigm. Two modes share no layout code —
they are different HTML skeletons.

---

## analysis

**Character:** Scrollable multi-section dashboard. Left sidebar navigation.
Fixed topbar. Sections stack vertically; user scrolls and jumps via nav.

**Best for:** Return-rate reports, selling-point analysis, monthly KPI dashboards,
any report where the reader wants to navigate between data sections non-linearly.

**Demo file:** `demos/demo-A-analysis-solid.html`, `demos/demo-B-analysis-ocean.html`,
`demos/demo-E-analysis-iceglass.html`

### HTML Skeleton

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Report Title</title>
  <!-- Font import: see dimensions/typography.md -->
  <style>
    /* ─── STYLE CONFIG ─────────────────────────────────────────
       Mode       : analysis
       ...
    ──────────────────────────────────────────────────────────── */
    /* :root variables: see dimensions/palette.md */
    /* Layout */
    body { font-family:var(--ff); background:var(--bg); color:var(--text); }
    .sidebar { position:fixed; top:0; left:0; width:var(--nav); height:100vh;
               background:var(--dark); z-index:200; overflow-y:auto;
               display:flex; flex-direction:column; }
    .topbar  { position:fixed; top:0; left:var(--nav); right:0; height:var(--top);
               background:var(--dark); z-index:100; }
    .main    { margin-left:var(--nav); padding-top:var(--top); }
    .section { padding:26px 32px 30px; border-bottom:1px solid var(--c-border); }
    /* Card, reveal, chart, etc: see references/components-analysis.md */
  </style>
</head>
<body>
  <!-- Custom cursor (optional, expressive motion only) -->
  <div id="cursor-dot"></div>
  <div id="cursor-ring"></div>

  <!-- Cover page -->
  <div id="cover"><!-- see references/components-analysis.md #cover --></div>

  <!-- Sidebar navigation -->
  <nav class="sidebar" id="sidebar">
    <!-- Brand block -->
    <div class="sb-brand">Report Title</div>
    <!-- Style Config display block -->
    <div class="sb-cfg">
      <div class="sb-cfg-t">STYLE CONFIG</div>
      <pre class="sb-cfg-pre">...</pre>
    </div>
    <!-- Nav links: one per section -->
    <a class="sb-link active" href="#s0">概览 Overview</a>
    <a class="sb-link" href="#s1">趋势 Trend</a>
    <!-- ... -->
  </nav>

  <!-- Fixed topbar -->
  <div class="topbar" id="topbar">
    <span class="tb-t">Report Title</span>
    <span class="tb-badge">BADGE TEXT</span>
  </div>

  <!-- Main content -->
  <div class="main">
    <section class="section" id="s0"><!-- Overview --></section>
    <section class="section" id="s1"><!-- Section 1 --></section>
    <!-- ... -->
  </div>

  <script src="https://cdn.jsdelivr.net/npm/echarts@5/dist/echarts.min.js"></script>
  <script>/* all JS inline */</script>
</body>
</html>
```

### Section structure (analysis)

```
#cover       Cover page: animated KPI counters + particle canvas (optional)
#s0          Overview: 8-metric KPI strip + 4-card key insights grid
#s1          Primary trend / time-series
#s2          Pareto / ranked breakdown
#s3          Geographic or dimensional breakdown (optional)
#s4–sN       Domain-specific sections (2–4 more)
#sN+1        Action recommendations (optional)
```

Keep to 5–8 sections. Announce the structure before coding.

### Analysis layout rules

- Charts go **full-width** first
- Below chart: `g55` grid — left 2×2 insight strips, right data table
- Never two charts side-by-side (height mismatch)
- KPI strip: 8 metrics in one row (responsive: 4→2 cols on mobile)
- Nav `active` state: tracked via IntersectionObserver (see `references/animations.md`)

---

## narrative

**Character:** Full-viewport scroll-snap slides. One message per slide.
No sidebar. Reader "flips" through pages rather than scrolling.

**Best for:** Portfolio showcases, demo reports, executive presentations,
brand intelligence reports displayed to external audiences.

**Demo file:** `demos/demo-C-narrative-glass.html`, `demos/demo-D-narrative-editorial.html`

### HTML Skeleton

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Report Title</title>
  <!-- Font import: see dimensions/typography.md -->
  <style>
    /* ─── STYLE CONFIG ─────────────────────────────────────────
       Mode       : narrative
       ...
    ──────────────────────────────────────────────────────────── */
    /* :root variables: see dimensions/palette.md */
    html { scroll-snap-type:y mandatory; scroll-behavior:smooth; height:100%; }
    body { height:100%; overflow-x:hidden; font-family:var(--ff); }
    .slide {
      width:100vw; height:100vh; height:100dvh;
      scroll-snap-align:start;
      overflow:hidden;
      display:flex; flex-direction:column;
      position:relative;
    }
    /* Slide number (bottom-right) */
    .sn { position:absolute; bottom:20px; right:24px;
          font-family:var(--fm); font-size:10px; color:var(--light); letter-spacing:.1em; }
    /* Navigation dots (optional) */
    .nav-dots { position:fixed; right:20px; top:50%; transform:translateY(-50%);
                z-index:100; display:flex; flex-direction:column; gap:8px; }
    .nav-dot { width:6px; height:6px; border-radius:50%; background:var(--bd); cursor:pointer; transition:all .3s; }
    .nav-dot.on { background:var(--accent); transform:scale(1.4); }
  </style>
</head>
<body>
  <!-- Slide 1: Cover / Title -->
  <section class="slide slide-cover" id="sl0">
    <!-- Full-viewport cover with title + subtitle + data chips -->
  </section>

  <!-- Slide 2: Key insight or overview -->
  <section class="slide" id="sl1">
    <!-- Single focus: one chart OR one key message + 2-3 metrics -->
  </section>

  <!-- ... more slides ... -->

  <!-- Last slide: Summary / CTA -->
  <section class="slide slide-end" id="slN">
    <!-- Key takeaways + closing -->
  </section>

  <!-- Navigation dots -->
  <div class="nav-dots" id="nav-dots"></div>

  <script src="https://cdn.jsdelivr.net/npm/echarts@5/dist/echarts.min.js"></script>
  <script>/* all JS inline */</script>
</body>
</html>
```

### Slide structure (narrative)

```
sl0    Cover: Title + subtitle + 3 key data chips
sl1    Problem or context slide
sl2    Key metric / hero number
sl3    Trend chart slide
sl4    Breakdown / comparison
sl5    Insight or finding #1
sl6    Insight or finding #2
sl7    (optional deeper data)
slN    Summary + action CTA
```

6–12 slides. One chart max per slide. One core message per slide.

### Narrative layout rules

- `scroll-snap-type: y mandatory` on `html`, `scroll-snap-align: start` on every `.slide`
- Every slide `height: 100vh; height: 100dvh; overflow: hidden`
- Content must fit within the viewport — no scrolling inside slides
- No sidebar; navigation dots on right edge (optional)
- Slide number in bottom-right corner
- Charts: max 60–70vh height; always leave room for title + context text

### Narrative JS: scroll nav & active dots

```js
// Generate navigation dots
const slides = document.querySelectorAll('.slide');
const dotsEl = document.getElementById('nav-dots');
slides.forEach((_, i) => {
  const d = document.createElement('div');
  d.className = 'nav-dot' + (i === 0 ? ' on' : '');
  d.onclick = () => slides[i].scrollIntoView({ behavior: 'smooth' });
  dotsEl.appendChild(d);
});

// Track active slide via IntersectionObserver
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

// Keyboard navigation
document.addEventListener('keydown', e => {
  const idx = Array.from(slides).findIndex(s => {
    const r = s.getBoundingClientRect();
    return r.top >= -10 && r.top <= 10;
  });
  if (e.key === 'ArrowDown' && idx < slides.length - 1)
    slides[idx + 1].scrollIntoView({ behavior: 'smooth' });
  if (e.key === 'ArrowUp' && idx > 0)
    slides[idx - 1].scrollIntoView({ behavior: 'smooth' });
});
```
