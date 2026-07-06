# Dimension: Typography

Four font stacks. Each defines: display font, body font, monospace/label font,
a Google Fonts import URL, and the full type scale using CSS variables.

---

## serif

**Character:** Elegance and authority. Contrast between serif display and
clean body text creates a premium, editorial feel.

**Best with:** warm-green, slate-warm palettes. Analysis or narrative mode.

**Font pair:** Playfair Display (display/headings) + Noto Serif SC (body) + Space Mono (mono)

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=Noto+Serif+SC:wght@400;600;700&family=Noto+Sans+SC:wght@300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```

```css
:root {
  --ff: 'Noto Sans SC', 'Noto Serif SC', sans-serif;    /* body */
  --fh: 'Playfair Display', 'Noto Serif SC', serif;      /* headings/display */
  --fm: 'Space Mono', monospace;                         /* labels/mono */
}
```

**Type scale:**

| Role | Font | Size | Weight | Color |
|------|------|------|--------|-------|
| Cover title | `--fh` | `clamp(2.8rem, 5vw, 4.5rem)` | 900 | `--dark` / `--text` |
| Section title | `--fh` | 18px | 700 | `--text` |
| Card title | `--fh` | 14.5px | 700 | `--text` |
| Numeric value | `--fm` | 1.5–2.2rem | 700 | `--text` |
| Body text | `--ff` | 13.5–14px | 400–500 | `--text` |
| Label (uppercase) | `--fm` | 9–11px | 700 | `--light`, letter-spacing: 1.5px |
| Subtitle/caption | `--ff` | 11.5–12px | 500 | `--muted` |

```css
/* Section title */
.sec-title {
  font-family: var(--fh);
  font-size: 18px; font-weight: 700; color: var(--text);
}
/* Card title */
.card-title {
  font-family: var(--fh);
  font-size: 14.5px; font-weight: 700; color: var(--text);
}
/* KPI value */
.kpi-val {
  font-family: var(--fm);
  font-size: 1.5rem; font-weight: 700; color: var(--text); line-height: 1;
}
/* Label */
.label {
  font-family: var(--fm);
  font-size: 10px; font-weight: 700; text-transform: uppercase;
  letter-spacing: 1.5px; color: var(--light);
}
```

---

## sans

**Character:** Modern, clean, universally readable. Numbers rendered in
Montserrat for weight; body in Inter for legibility; Chinese in Noto Sans SC.

**Best with:** ocean-blue, warm-green. Analysis mode.

**Font pair:** Montserrat (numbers/display) + Inter (body EN) + Noto Sans SC (body ZH) + Space Mono (labels)

```html
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&family=Inter:wght@300;400;500;600;700&family=Noto+Sans+SC:wght@300;400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```

```css
:root {
  --ff:   'Inter', 'Noto Sans SC', sans-serif;           /* body */
  --fnum: 'Montserrat', sans-serif;                      /* numbers/KPI values */
  --fm:   'Space Mono', monospace;                       /* labels */
}
```

**Type scale:**

| Role | Font | Size | Weight |
|------|------|------|--------|
| Cover title | `--fnum` | `clamp(2.8rem, 5vw, 4.5rem)` | 900 |
| Section title | `--ff` | 18px | 700 |
| KPI value | `--fnum` | 1.5–2.2rem | 700 |
| Body | `--ff` | 14px | 400 |
| Label | `--fm` | 9–10px | 700, uppercase, letter-spacing 1.2px |

---

## mono-heavy

**Character:** Space Mono dominates — technical, data-terminal aesthetic.
Use when the report audience is technical and the "code/data" feeling is intentional.

**Best with:** dark-glass, ocean-blue. Narrative or analysis mode.

**Font pair:** Space Mono (display + labels + values) + Noto Sans SC (body only)

```html
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Noto+Sans+SC:wght@300;400;500&display=swap" rel="stylesheet">
```

```css
:root {
  --ff: 'Space Mono', 'Noto Sans SC', monospace;    /* everything */
  --fh: 'Space Mono', monospace;                    /* headings */
  --fm: 'Space Mono', monospace;                    /* labels */
}
/* Body paragraphs fall back to Noto Sans SC for readability */
.body-text { font-family: 'Noto Sans SC', sans-serif; }
```

**Type scale adjustments for mono-heavy:**

- Cover title: `font-size: clamp(2rem, 4vw, 3.5rem)` — mono is wider, needs slightly smaller
- All caps labels feel native — lean into `text-transform: uppercase`
- Letter-spacing `0.05–0.12em` on body text improves readability at smaller sizes
- Numeric values: keep at `font-size: 1.4rem` max — mono numerals are wide

---

## glass-round

**Character:** Montserrat's geometric, rounded letter forms pair with
幼圆 (YouYuan) Chinese for a soft, premium bilingual feel. Purpose-designed
for the ice-glass palette and glass-round UI style.

**Best with:** ice-glass palette + glass-round UI style (this is its dedicated home)
**Also works with:** dark-glass for a less "icy" interpretation

**Font pair:** Montserrat (all EN/numeric) + 幼圆/YouYuan (all ZH)

```html
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
<!-- YouYuan / 幼圆 is a system font on macOS/Windows; no Google Fonts URL needed -->
```

```css
:root {
  --ff: 'Montserrat', '幼圆', 'YouYuan', 'PingFang SC', sans-serif;
  --fm: 'Montserrat', '幼圆', 'YouYuan', monospace;
}
```

**Type scale for glass-round:**

| Role | Size | Weight | Extra |
|------|------|--------|-------|
| Cover title h1 | `clamp(2.2rem, 4.2vw, 3.8rem)` | 900 | `letter-spacing: -.03em` |
| Cover keyword span | same | 900 | `color: #3E5661` |
| Section title | 20px | 900 | `letter-spacing: -.02em` |
| KPI value | 36px | 900 | `letter-spacing: -.03em; line-height: 1` |
| KPI unit | 9px | 700 | uppercase, `letter-spacing: .5px` |
| KPI label | 9px | 700 | uppercase, `letter-spacing: 1.5px`, `rgba(47,65,74,.5)` |
| Body | 13–14px | 500 | `line-height: 1.72` |
| Caption/label | 10px | 700 | uppercase, `letter-spacing: 2px`, `rgba(47,65,74,.45)` |
| Badge/tag | 9–10px | 600–700 | `letter-spacing: .08em` |

```css
/* Glass-Round specific type rules */
.cv-h1 {
  font-family: var(--ff);
  font-size: clamp(2.2rem, 4.2vw, 3.8rem);
  font-weight: 900; line-height: 1.06; letter-spacing: -.03em;
  color: #2F414A;
}
.ks-val {
  font-family: var(--ff);
  font-size: 36px; font-weight: 900;
  color: var(--c-deep); line-height: 1; letter-spacing: -.03em;
}
.ks-lbl {
  font-family: var(--ff);
  font-size: 9px; letter-spacing: 1.5px;
  text-transform: uppercase; color: rgba(47,65,74,.5); font-weight: 700;
}
/* Section header label (eyebrow) */
.sh-tag {
  font-family: var(--ff);
  font-size: 10px; letter-spacing: 2px;
  text-transform: uppercase; color: rgba(255,255,255,.45); font-weight: 700;
}
.sh-title {
  font-size: 20px; font-weight: 900; color: var(--c-deep); letter-spacing: -.02em;
}
```
