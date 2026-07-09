# Demos

Five reference reports demonstrating all major style config combinations.
Each is a complete, self-contained HTML file — open in browser to preview.

---

## demo-A-analysis-solid.html

```
╔═ STYLE CONFIG v3.0 ════════════╗
  Mode       │ analysis
  Palette    │ warm-green
  UI Style   │ solid
  Typography │ serif   (Playfair Display + Noto Serif SC)
  Motion     │ standard
╚════════════════════════════════╝
```

**Character:** Earthy professional. Warm amber + forest green. Solid opaque cards.
Playfair Display section titles. Counter animation on cover, ECharts on scroll.
**Use as reference for:** Internal monthly reports, return analysis, sales dashboards.

---

## demo-B-analysis-ocean.html

```
╔═ STYLE CONFIG v3.0 ════════════╗
  Mode       │ analysis
  Palette    │ ocean-blue
  UI Style   │ solid
  Typography │ sans   (Montserrat num / Inter body)
  Motion     │ standard
╚════════════════════════════════╝
```

**Character:** Cool, corporate. Blue tones on near-black. Sans-serif throughout.
Montserrat for numeric values, Inter for body text.
**Use as reference for:** External business reports, product analytics, investor decks.

---

## demo-C-narrative-glass.html

```
╔═ STYLE CONFIG v3.0 ════════════╗
  Mode       │ narrative
  Palette    │ dark-glass
  UI Style   │ glass
  Typography │ sans
  Motion     │ expressive
╚════════════════════════════════╝
```

**Character:** Full-viewport scroll-snap slides. Smoky blue dark glass. Particle
background on cover. Stagger entrance, 3D card hover, rotating decorations.
**Use as reference for:** Portfolio showcases, demo presentations, narrative reports.

---

## demo-D-narrative-editorial.html

```
╔═ STYLE CONFIG v3.0 ════════════╗
  Mode       │ narrative
  Palette    │ slate-warm
  UI Style   │ editorial
  Typography │ serif   (Playfair Display + Noto Serif SC)
  Motion     │ standard
╚════════════════════════════════╝
```

**Character:** Full-viewport slides with editorial left-bar card style. Cream/warm
tones. Pull quotes. Serif typography creates a magazine-report feel.
**Use as reference for:** Brand strategy reports, narrative executive presentations.

---

## demo-E-analysis-iceglass.html

```
╔═ STYLE CONFIG v3.0 ════════════╗
  Mode       │ analysis
  Palette    │ ice-glass  (CamPulse 冰透玻璃风格 v6)
  UI Style   │ glass-round  (高透白玻璃 + 超大圆角)
  Typography │ glass-round  (Montserrat + 幼圆/YouYuan)
  Motion     │ standard
╚════════════════════════════════╝
```

**Character:** Fixed cool-teal gradient background. Frosted glass cards float
above it as the user scrolls. 24px corner radius everywhere. Montserrat + 幼圆
font pair. Low-saturation teal color family throughout.
**Use as reference for:** Brand intelligence reports, competitive analysis, CamPulse-style reports.

---

## phase0-style-selector.html

Interactive 5-step style selector. Users click through each axis (Mode, Palette,
UI Style, Typography, Motion) and receive a copyable Style Config block at the end.

**Use:** This file is the canonical Phase 0 artifact. When the user has not yet
provided a complete Style Config, output this exact HTML file first and stop.
Tell the user to complete the 5 steps, copy the generated Style Config block,
and paste it back before any report generation begins.

---

## Quick Lookup: Which demo to reference?

| User asks for... | Reference demo |
|-----------------|---------------|
| 退货分析 / 月报 / 数据报告 | demo-A |
| 商务汇报 / 对外报告 | demo-B |
| 作品集 / Portfolio / 技术展示 | demo-C |
| 品牌报告 / 编辑风格 | demo-D |
| CamPulse / 冰透 / 品牌情报 / ice glass | demo-E |
