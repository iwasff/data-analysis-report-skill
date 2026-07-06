# Components: Analysis Mode

Copy-paste HTML + CSS blocks for all Analysis mode UI elements.
All examples use Warm-Green palette variables — swap for your chosen palette.

---

## Sidebar

```html
<nav class="sidebar" id="sidebar">
  <!-- Brand -->
  <div class="sb-top">
    <div class="sb-brand">报告名称</div>
    <div class="sb-sub">DATA ANALYSIS REPORT</div>
  </div>

  <!-- Style Config display -->
  <div class="sb-cfg">
    <div class="sb-cfg-t">STYLE CONFIG</div>
    <pre class="sb-cfg-pre">╔═ STYLE CONFIG v3.0 ════════╗
  Mode       │ analysis
  Palette    │ warm-green
  UI Style   │ solid
  Typography │ serif
  Motion     │ standard
╚════════════════════════════╝</pre>
  </div>

  <!-- Section divider label -->
  <div class="sb-sec-l">SECTIONS</div>

  <!-- Nav links — one per section -->
  <a class="sb-link active" href="#cover">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="14" height="14"><rect x="3" y="3" width="18" height="18" rx="2"/></svg>
    概览
  </a>
  <a class="sb-link" href="#s1">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="14" height="14"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>
    趋势分析
  </a>
  <a class="sb-link" href="#s2">
    <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="14" height="14"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>
    分类明细
  </a>
  <!-- Add more links per section -->
</nav>
```

```css
.sidebar {
  position: fixed; top: 0; left: 0; width: var(--nav); height: 100vh;
  background: var(--dark); z-index: 200; overflow-y: auto;
  display: flex; flex-direction: column; padding: 22px 0 16px;
}
.sb-top { padding: 0 16px 16px; border-bottom: 1px solid rgba(255,255,255,.08); margin-bottom: 12px; }
.sb-brand { font-family: var(--fh); font-size: 14px; font-weight: 700; color: #C8D9A8; line-height: 1.3; }
.sb-sub { font-size: 9px; color: rgba(200,217,168,.4); margin-top: 4px; font-family: var(--fm); letter-spacing: .1em; }
.sb-cfg { margin: 0 14px 14px; background: rgba(163,177,138,.1); border: 1px solid rgba(163,177,138,.18); border-radius: 8px; padding: 10px 12px; }
.sb-cfg-t { font-family: var(--fm); font-size: 9px; letter-spacing: .14em; color: var(--sok); margin-bottom: 6px; font-weight: 700; text-transform: uppercase; }
.sb-cfg-pre { font-family: var(--fm); font-size: 9.5px; color: rgba(200,217,168,.6); line-height: 1.7; background: none; border: none; padding: 0; white-space: pre; }
.sb-sec-l { font-family: var(--fm); font-size: 9px; color: rgba(200,217,168,.3); letter-spacing: .12em; padding: 0 16px; margin-bottom: 6px; text-transform: uppercase; font-weight: 700; }
.sb-link {
  display: flex; align-items: center; gap: 9px;
  padding: 8px 16px; font-size: 12.5px; color: rgba(200,217,168,.55);
  border-left: 2px solid transparent; text-decoration: none;
  transition: all .2s; font-family: var(--ff); font-weight: 500;
}
.sb-link:hover { color: #C8D9A8; background: rgba(255,255,255,.04); }
.sb-link.active { color: #C8D9A8; border-left-color: var(--sd); background: rgba(208,152,106,.07); font-weight: 700; }
```

---

## Topbar

```html
<div class="topbar" id="topbar">
  <div class="tb-left">
    <span class="tb-t">报告标题</span>
    <span class="tb-sep"></span>
    <span class="tb-badge">2024 Q4</span>
  </div>
  <div class="tb-meta">最后更新 2025-01-15</div>
</div>
```

```css
.topbar {
  position: fixed; top: 0; left: var(--nav); right: 0; height: var(--top);
  background: rgba(41,61,51,.97); border-bottom: 1px solid rgba(163,177,138,.2);
  z-index: 100; display: flex; align-items: center; justify-content: space-between;
  padding: 0 24px;
}
.tb-left { display: flex; align-items: center; gap: 12px; }
.tb-t { font-family: var(--fh); font-size: 13.5px; font-weight: 600; color: #C8D9A8; font-style: italic; }
.tb-sep { width: 1px; height: 12px; background: rgba(200,217,168,.2); }
.tb-badge {
  font-family: var(--fm); font-size: 10px; padding: 3px 10px; border-radius: 100px;
  background: rgba(208,152,106,.15); color: var(--sd); border: 1px solid rgba(208,152,106,.25);
  font-weight: 700;
}
.tb-meta { font-family: var(--fm); font-size: 10px; color: rgba(200,217,168,.35); letter-spacing: .06em; }
```

---

## Cover Section

```html
<div class="cover-sec" id="cover">
  <!-- Decorative ring (expressive motion only) -->
  <div class="cover-deco"></div>
  <!-- Optional particle canvas -->
  <canvas id="cover-canvas" style="position:absolute;inset:0;width:100%;height:100%;pointer-events:none;"></canvas>

  <div class="cover-content">
    <!-- Eyebrow -->
    <div class="cv-ew">
      <span></span><!-- left line via CSS -->
      DATA ANALYSIS REPORT · 2025
    </div>
    <!-- Main title -->
    <h1 class="cv-h1">
      报告<span class="kw">主标题</span><br>副标题补充
    </h1>
    <p class="cv-sub">报告时间范围 · 数据来源说明</p>

    <!-- KPI chips row -->
    <div class="cv-stats">
      <div class="cvs">
        <span class="cvs-n" data-count="14.3" data-suffix="%">0%</span>
        <span class="cvs-l">核心指标一</span>
      </div>
      <div class="cvs-div"></div>
      <div class="cvs">
        <span class="cvs-n" data-count="3842">0</span>
        <span class="cvs-l">核心指标二</span>
      </div>
      <div class="cvs-div"></div>
      <div class="cvs">
        <span class="cvs-n" data-count="8">0</span>
        <span class="cvs-l">分析维度</span>
      </div>
    </div>
  </div>
</div>
```

```css
.cover-sec {
  min-height: 90vh; background: var(--dark);
  display: flex; align-items: center;
  padding: 60px 56px; position: relative; overflow: hidden;
}
.cover-deco {
  position: absolute; right: -80px; top: 50%; transform: translateY(-50%);
  width: 500px; height: 500px; border-radius: 50%;
  background: radial-gradient(circle, rgba(208,152,106,.08) 0%, transparent 70%);
  pointer-events: none;
}
.cover-content { position: relative; z-index: 1; max-width: 660px; }
.cv-ew {
  font-family: var(--fm); font-size: 11px; letter-spacing: .18em;
  text-transform: uppercase; color: rgba(200,217,168,.5);
  display: flex; align-items: center; gap: 12px; margin-bottom: 22px;
}
.cv-ew::before { content: ''; width: 18px; height: 1px; background: var(--sd); }
.cv-h1 {
  font-family: var(--fh); font-size: clamp(2.8rem, 5vw, 4.5rem);
  font-weight: 900; line-height: 1.06; letter-spacing: -.025em;
  color: #EDE8C0; margin-bottom: 14px;
}
.cv-h1 .kw { color: var(--sd); }
.cv-sub { font-size: 14px; color: rgba(200,217,168,.45); margin-bottom: 38px; }
.cv-stats { display: flex; align-items: center; gap: 0; }
.cvs { padding: 0 24px; }
.cvs:first-child { padding-left: 0; }
.cvs-n { font-family: var(--fm); font-size: 2.2rem; font-weight: 700; color: var(--sd); line-height: 1; display: block; }
.cvs-l { font-size: 11px; color: rgba(200,217,168,.4); margin-top: 5px; display: block; font-family: var(--fm); letter-spacing: .04em; }
.cvs-div { width: 1px; height: 40px; background: rgba(200,217,168,.15); }
```

---

## Section Header

```html
<div class="sec-head reveal">
  <span class="sec-title">Section Title</span>
  <span class="sec-badge">BADGE · DATE</span>
</div>
```

```css
.sec-head { display: flex; align-items: baseline; gap: 12px; margin-bottom: 18px; }
.sec-title { font-family: var(--fh); font-size: 18px; font-weight: 700; color: var(--text); }
.sec-badge {
  font-family: var(--fm); font-size: 10px; padding: 2px 9px; border-radius: 4px;
  background: rgba(163,177,138,.18); color: var(--muted); font-weight: 700;
  letter-spacing: .06em;
}
```

---

## KPI Strip (8-card row)

```html
<div class="kpi-strip reveal">
  <div class="ks" style="--ks-ac:var(--sd)">
    <div class="ks-lbl">METRIC LABEL</div>
    <div class="ks-val">14.3<span class="ks-u">%</span></div>
    <div class="ks-sub">↑ vs prev period</div>
  </div>
  <!-- repeat ×8 — adjust --ks-ac per card -->
</div>
```

```css
.kpi-strip {
  display: grid; grid-template-columns: repeat(4, 1fr); gap: 10px; margin-bottom: 16px;
}
@media (max-width: 900px) { .kpi-strip { grid-template-columns: repeat(2, 1fr); } }

.ks {
  background: var(--card); border-radius: var(--r);
  box-shadow: var(--shadow); padding: 14px 16px 16px;
  position: relative; overflow: hidden;
  transition: transform .2s, box-shadow .2s;
}
.ks:hover { transform: translateY(-2px); box-shadow: var(--shadow-h); }
.ks::before {
  content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px;
  background: var(--ks-ac, var(--sn)); border-radius: var(--r) var(--r) 0 0;
}
.ks-lbl {
  font-family: var(--fm); font-size: 9px; letter-spacing: 1.5px;
  text-transform: uppercase; color: var(--light); margin-bottom: 10px; font-weight: 700;
}
.ks-val {
  font-family: var(--fm); font-size: 1.5rem; font-weight: 700;
  color: var(--text); line-height: 1; margin-bottom: 6px;
}
.ks-u { font-size: 12px; color: var(--muted); margin-left: 2px; }
.ks-sub { font-size: 11px; color: var(--light); font-weight: 500; }
```

---

## Key Insights Grid (4-card, 2×2)

```html
<div class="g2 reveal">
  <div class="ins-card">
    <div class="ins-icon">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="18" height="18"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>
    </div>
    <div class="ins-card-body">
      <div class="ins-card-title">洞察标题</div>
      <div class="ins-card-text">支撑这个洞察的具体数据说明，1-2句话。</div>
    </div>
  </div>
  <!-- ×4 -->
</div>
```

```css
.ins-card {
  display: flex; gap: 14px; align-items: flex-start;
  background: var(--card); border-radius: var(--r);
  padding: 16px 18px; box-shadow: var(--shadow);
  border-left: 3px solid var(--sd);
  transition: transform .2s, box-shadow .2s;
}
.ins-card:hover { transform: translateY(-2px); box-shadow: var(--shadow-h); }
.ins-icon {
  width: 32px; height: 32px; border-radius: 8px; flex-shrink: 0;
  background: rgba(208,152,106,.12); display: flex; align-items: center; justify-content: center;
  color: var(--sd);
}
.ins-card-title { font-family: var(--fh); font-size: 13.5px; font-weight: 700; color: var(--text); margin-bottom: 5px; }
.ins-card-text  { font-size: 12.5px; color: var(--muted); line-height: 1.6; }
```

---

## Insight Strips (`.ins`)

For inline findings below charts. Left border color = severity.

```html
<div class="ins danger reveal d1">
  <div class="ins-head">P0 — 问题标题</div>
  <div class="ins-body">具体说明，直接指向数据，1-2 句。</div>
</div>
<div class="ins warn reveal d2">
  <div class="ins-head">P1 — 关注点</div>
  <div class="ins-body">说明。</div>
</div>
<div class="ins ok reveal d3">
  <div class="ins-head">亮点</div>
  <div class="ins-body">说明。</div>
</div>
```

```css
.ins {
  background: var(--card); border-radius: 0 var(--r) var(--r) 0;
  border-left: 3px solid var(--border); padding: 12px 16px;
  box-shadow: var(--shadow); margin-bottom: 10px;
}
.ins.danger  { border-left-color: var(--sd);  background: #FEF7ED; }
.ins.warn    { border-left-color: var(--sw);  background: #FEF9EC; }
.ins.ok      { border-left-color: var(--sok); background: #F2F7EE; }
.ins.info    { border-left-color: var(--sn);  }
.ins-head { font-family: var(--fh); font-size: 13px; font-weight: 700; color: var(--text); margin-bottom: 5px; }
.ins-body { font-size: 12.5px; color: var(--muted); line-height: 1.6; }
```

---

## Chart + Data Layout (standard section pattern)

```html
<!-- Full-width chart -->
<div class="chart-card reveal">
  <div class="chart-title">图表标题</div>
  <div class="chart-sub">副标题说明</div>
  <div id="chart-main" style="height:280px;"></div>
</div>

<!-- Below: 2-col (insight strips | data table) -->
<div class="g55 reveal">
  <!-- Left: insight strips -->
  <div>
    <div class="ins ok d1">...</div>
    <div class="ins warn d2">...</div>
    <div class="ins danger d3">...</div>
  </div>
  <!-- Right: data table -->
  <div class="card">
    <table class="dt">
      <thead><tr><th>维度</th><th>数值</th><th>环比</th></tr></thead>
      <tbody>
        <tr><td>A 类</td><td class="dt-num">14.3%</td><td class="mt-bad">↑2.1%</td></tr>
        <tr><td>B 类</td><td class="dt-num">8.7%</td><td class="mt-ok">↓1.2%</td></tr>
      </tbody>
    </table>
  </div>
</div>
```

```css
.chart-card { background: var(--card); border-radius: var(--r); box-shadow: var(--shadow); padding: 18px 20px; margin-bottom: 14px; }
.chart-title { font-family: var(--fh); font-size: 14px; font-weight: 700; color: var(--text); margin-bottom: 3px; }
.chart-sub { font-size: 11.5px; color: var(--light); margin-bottom: 12px; }

/* Data table */
.dt { width: 100%; border-collapse: collapse; font-size: 12.5px; }
.dt th { font-family: var(--fm); font-size: 9px; letter-spacing: 1px; text-transform: uppercase; color: var(--light); font-weight: 700; padding: 7px 10px; text-align: left; border-bottom: 1px solid var(--border); }
.dt td { padding: 8px 10px; border-bottom: 1px solid var(--border-lt); color: var(--text); vertical-align: middle; }
.dt tbody tr:hover { background: rgba(163,177,138,.06); }
.dt-num { font-family: var(--fm); font-weight: 700; }
.mt-bad  { color: var(--sd); font-weight: 700; font-family: var(--fm); }
.mt-warn { color: #7A5A00; font-weight: 700; font-family: var(--fm); }
.mt-ok   { color: var(--primary); font-weight: 700; font-family: var(--fm); }

/* Grids */
.g2  { display: grid; grid-template-columns: 1fr 1fr; gap: 13px; }
.g3  { display: grid; grid-template-columns: repeat(3,1fr); gap: 13px; }
.g55 { display: grid; grid-template-columns: 1fr 1fr; gap: 13px; align-items: start; }
.g73 { display: grid; grid-template-columns: 7fr 3fr; gap: 13px; align-items: start; }
```

---

## Action Cards (P0/P1/P2 recommendation blocks)

```html
<div class="g2 reveal">
  <div class="action-card p0">
    <div class="ac-head">
      <span class="ac-priority">P0</span>
      <span class="ac-title">立即执行的建议</span>
    </div>
    <div class="ac-body">具体措施说明，1-2句。</div>
    <div class="ac-meta">负责方 · 截止时间</div>
  </div>
  <div class="action-card p1">...</div>
  <div class="action-card p2">...</div>
  <div class="action-card p2">...</div>
</div>
```

```css
.action-card {
  background: var(--card); border-radius: var(--r); padding: 18px 20px;
  box-shadow: var(--shadow); border-left: 4px solid var(--border);
  transition: transform .2s, box-shadow .2s;
}
.action-card:hover { transform: translateY(-2px); box-shadow: var(--shadow-h); }
.action-card.p0 { border-left-color: var(--sd); }
.action-card.p1 { border-left-color: var(--sw); }
.action-card.p2 { border-left-color: var(--sn); }
.ac-head { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
.ac-priority {
  font-family: var(--fm); font-size: 10px; font-weight: 700;
  padding: 2px 8px; border-radius: 4px; letter-spacing: .04em;
}
.action-card.p0 .ac-priority { background: rgba(208,152,106,.2); color: var(--sd); }
.action-card.p1 .ac-priority { background: rgba(227,193,152,.2); color: #7A5A00; }
.action-card.p2 .ac-priority { background: rgba(204,206,168,.2); color: var(--primary); }
.ac-title { font-family: var(--fh); font-size: 14px; font-weight: 700; color: var(--text); }
.ac-body  { font-size: 13px; color: var(--muted); line-height: 1.65; margin-bottom: 12px; }
.ac-meta  { font-family: var(--fm); font-size: 10px; color: var(--light); letter-spacing: .04em; }
```

---

## SVG Icon Library

Use these inline SVGs — no emoji, no icon fonts.

```html
<!-- Dashboard / Overview -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/></svg>

<!-- Trend / Line chart -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>

<!-- Bar chart -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><line x1="18" y1="20" x2="18" y2="10"/><line x1="12" y1="20" x2="12" y2="4"/><line x1="6" y1="20" x2="6" y2="14"/></svg>

<!-- Alert / Warning -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><path d="M10.29 3.86L1.82 18a2 2 0 001.71 3h16.94a2 2 0 001.71-3L13.71 3.86a2 2 0 00-3.42 0z"/><line x1="12" y1="9" x2="12" y2="13"/><line x1="12" y1="17" x2="12.01" y2="17"/></svg>

<!-- Check / OK -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><polyline points="20 6 9 17 4 12"/></svg>

<!-- Globe / Map -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 014 10 15.3 15.3 0 01-4 10 15.3 15.3 0 01-4-10 15.3 15.3 0 014-10z"/></svg>

<!-- Info -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" width="16" height="16"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12"/><line x1="12" y1="16" x2="12.01" y2="16"/></svg>

<!-- Arrow up (increase) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" width="12" height="12"><line x1="12" y1="19" x2="12" y2="5"/><polyline points="5 12 12 5 19 12"/></svg>

<!-- Arrow down (decrease) -->
<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" width="12" height="12"><line x1="12" y1="5" x2="12" y2="19"/><polyline points="19 12 12 19 5 12"/></svg>
```

---

## Heatmap Table

```html
<table class="heatmap">
  <thead>
    <tr>
      <th class="ht-corner"></th>
      <th>1月</th><th>2月</th><th>3月</th><!-- ... -->
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>品类A</th>
      <td style="--v:0.85">8.5%</td>
      <td style="--v:0.0">—</td><!-- empty: use warm color -->
      <td style="--v:0.45">4.5%</td>
    </tr>
  </tbody>
</table>
```

```css
.heatmap { width: 100%; border-collapse: collapse; font-size: 12px; }
.heatmap th { font-family: var(--fm); font-size: 9px; text-transform: uppercase; letter-spacing: 1px; color: var(--light); padding: 6px 8px; font-weight: 700; }
.heatmap .ht-corner { width: 80px; }
.heatmap td {
  padding: 6px 8px; text-align: center; border-radius: 4px;
  font-family: var(--fm); font-weight: 700; font-size: 11.5px;
  /* Interpolate between empty and danger based on --v (0–1) */
  background: color-mix(in srgb, #D0986A calc(var(--v, 0) * 70%), #EDE8C0);
  color: color-mix(in srgb, #7A3800 calc(var(--v, 0) * 100%), var(--light));
}
/* No-data cells: warm empty, not grey */
.heatmap td.empty { background: #EDE8C0; color: var(--border); }
```

---

## ECharts Base Config Snippets

Define once at top of `<script>`:

```js
// Shared tooltip style
const TT = {
  backgroundColor: 'rgba(41,61,51,.96)',
  borderColor: 'rgba(163,177,138,.3)',
  textStyle: { color: '#F5EAC5', fontSize: 12 },
  borderRadius: 8, padding: [10, 14]
};
// Axis label style
const sL  = { color: '#5A6650', fontSize: 11 };
// Split line style
const spL = { lineStyle: { color: 'rgba(163,177,138,.25)', type: 'dashed' } };
// Axis line style
const axL = { lineStyle: { color: 'rgba(163,177,138,.3)' } };
// Warm-Green chart colors
const C = {
  p0: '#D0986A', p1: '#E3C198', p2: '#CCCEA8', p3: '#A3B18A',
  green: '#3A5A40', teal: '#7EA090'
};
// Color sequence
const SEQ = ['#D0986A','#E3C198','#CCCEA8','#A3B18A','#7EA090','#658C6E','#588157','#3A5A40'];
```

Always call `window.addEventListener('resize', () => chart.resize())` per chart instance.
