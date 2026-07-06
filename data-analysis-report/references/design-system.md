# Design System Reference

Complete token system for all five palettes. Pick one per report — do not
mix tokens across palettes. All rules here are authoritative; `dimensions/palette.md`
has the same `:root` blocks with additional context.

**Default palette: warm-green.**

---

## Palette 1: Warm-Green (Default)

Earthy, professional. Warm amber on dark forest green.
**Best for:** Internal ops reports, return analysis, monthly reviews.

```css
:root {
  --bg:         #7EA090;   /* odd sections  */
  --bg-alt:     #EDE8C0;   /* even sections */
  --card:       #F9F3DC;   /* cards — always lighter than sections */
  --dark:       #293D33;   /* sidebar, cover, topbar */
  --primary:    #588157;
  --tag:        #D6E8BC;   /* table headers */
  --text:       #0F0F0D;
  --muted:      #3A4430;
  --light:      #5A7050;
  --border:     #A3B18A;
  --border-lt:  #C8D9A8;
  --sd:         #D0986A;   /* danger  */
  --sw:         #E3C198;   /* warning */
  --sn:         #CCCEA8;   /* neutral */
  --sok:        #A3B18A;   /* ok      */
  --shadow:     0 2px 8px  rgba(41,61,51,.10);
  --shadow-h:   0 6px 20px rgba(41,61,51,.16);
  --r:    10px; --nav: 220px; --top: 48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  --ff:   'Noto Sans SC', sans-serif;
  --fh:   'Playfair Display', 'Noto Serif SC', serif;
  --fm:   'Space Mono', monospace;
}
```

**10-color palette** (only these — no ad-hoc hex values):
`#D0986A` `#E3C198` `#F5EAC5` `#CCCEA8` `#A3B18A` `#7EA090` `#658C6E` `#588157` `#3A5A40` `#293D33`

**ECharts color sequence:** `['#D0986A','#E3C198','#CCCEA8','#A3B18A','#7EA090','#658C6E','#588157','#3A5A40']`

---

## Palette 2: Ocean-Blue

Clean, corporate. Cool blue tones on near-black.
**Best for:** External business reports, investor decks, product analytics.

```css
:root {
  --bg:         #4A7A96;
  --bg-alt:     #D8E8F0;
  --card:       #F0F8FC;
  --dark:       #1A2F3A;
  --primary:    #2E6DA4;
  --tag:        #C8DFF0;
  --text:       #0A0F14;
  --muted:      #2A3A48;
  --light:      #4A6A80;
  --border:     #7AA8C0;
  --border-lt:  #A8CCE0;
  --accent:     #5B8DB8;
  --accent2:    #7AAED4;
  --sd:         #906060;
  --sw:         #C8A870;
  --sn:         #8AAAC0;
  --sok:        #3A8A6A;
  --shadow:     0 2px 10px rgba(26,47,58,.12);
  --shadow-h:   0 8px 24px  rgba(26,47,58,.20);
  --r:    10px; --nav: 240px; --top: 48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  --ff:   'Inter', 'Noto Sans SC', sans-serif;
  --fnum: 'Montserrat', sans-serif;
  --fm:   'Space Mono', monospace;
}
```

**ECharts color sequence:** `['#906060','#C8A870','#8AAAC0','#3A8A6A','#2E6DA4','#4A7A96','#1A4A6A','#1A2F3A']`

---

## Palette 3: Slate-Warm

Editorial, modern. Amber accent on dark charcoal.
**Best for:** Brand analysis, narrative presentations, executive summaries.

```css
:root {
  --bg:         #EEEAE0;
  --bg-alt:     #E0DDD2;
  --bg3:        #F4F1E8;
  --card:       #F4EEE0;
  --dark:       #2A2A2A;
  --dark2:      #1E1E1E;
  --primary:    #7A6A4A;
  --warm:       #C17F4A;
  --warm2:      #D4AA70;
  --text:       #1A1A16;
  --muted:      #5A5548;
  --light:      #8A8070;
  --border:     #C0B898;
  --border-lt:  #D8D0B8;
  --sd:         #C17F4A;
  --sw:         #D4A860;
  --sn:         #B0A888;
  --sok:        #6A8A5A;
  --shadow:     0 2px 10px rgba(42,42,42,.10);
  --shadow-h:   0 8px 24px  rgba(42,42,42,.16);
  --r:    10px; --nav: 220px; --top: 48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  --ff:   'Noto Serif SC', 'Noto Sans SC', serif;
  --fh:   'Playfair Display', 'Noto Serif SC', serif;
  --fm:   'Space Mono', monospace;
}
```

**ECharts color sequence:** `['#C17F4A','#D4A860','#B0A888','#6A8A5A','#8A6A3A','#6A6A5A','#4A4A3A','#2A2A2A']`

---

## Palette 4: Dark-Glass

Smoky blue on near-black. Dramatic, immersive.
**Best for:** Portfolio showcases, narrative tech reports, demo presentations.

```css
:root {
  --bg:      #1a1f2e;
  --bg2:     #1f2438;
  --glass:   rgba(255,255,255,.055);
  --glassh:  rgba(255,255,255,.090);
  --bd:      rgba(255,255,255,.090);
  --bdh:     rgba(255,255,255,.180);
  --sl:      #7a9ab8;   /* primary accent */
  --sl2:     #9bb4cb;
  --sl3:     rgba(122,154,184,.15);
  --vi:      #9b94b8;   /* violet accent */
  --vi2:     rgba(155,148,184,.15);
  --em:      #6ab4d4;   /* emphasis */
  --em2:     rgba(106,180,212,.15);
  --t1:      #e2e8f4;   /* primary text */
  --t2:      #8a94a8;   /* secondary text */
  --t3:      #464f62;   /* muted text */
  --shadow:  0 4px 20px rgba(0,0,0,.4);
  --shadow-h:0 8px 40px rgba(0,0,0,.5);
  --r:   12px;
  --e1:  cubic-bezier(.16,1,.3,1);
  --e2:  cubic-bezier(.34,1.56,.64,1);
  --e3:  cubic-bezier(.4,0,.2,1);
  --ff:  'Inter', sans-serif;
  --fm:  'Space Mono', monospace;
}
body { background: var(--bg); color: var(--t1); }
```

**Card CSS:**
```css
.card {
  background: var(--glass);
  border: 1px solid var(--bd);
  border-radius: var(--r);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: var(--shadow);
}
```

**ECharts color sequence:** `['#7a9ab8','#9bb4cb','#6ab4d4','#9b94b8','#5a7a98','#4a6a88','#3a5a78','#2a4a68']`

---

## Palette 5: Ice-Glass（冰透玻璃）— CamPulse v6 Spec

Cool teal fixed-gradient background + frosted glass cards. Airy, luminous, premium.
**Best for:** Brand intelligence reports, competitive analysis, external showcase.
**Demo:** `demos/demo-E-analysis-iceglass.html`

### ⚠️ Architectural difference from palettes 1–4

| Property | Palettes 1–4 | Ice-Glass |
|----------|-------------|-----------|
| Background | Solid section colors | Fixed gradient — never scrolls |
| Cards | Opaque fill | Semi-transparent + `backdrop-filter` |
| Sections | Alternating color blocks | All transparent |
| Navbar | Dark solid | Solid `#2F414A` |
| Border radius | 10px | 24px (`--r`) |
| Fonts | Noto families | Montserrat + 幼圆 |
| Accent color | Saturated colors | Low-saturation teal family |

```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&display=swap');

:root {
  /* ── Core text colors ── */
  --c-deep:   #2F414A;   /* primary text + dark nav bg */
  --c-mid:    #5C7E8C;   /* secondary text + labels */
  --c-soft:   #7DA59C;   /* status, accents, timeline nodes */
  --c-muted:  #9BB8BC;   /* helper text */
  --c-nav:    #2F414A;   /* sidebar/topbar background */

  /* ── Glass card surfaces ── */
  --card:     rgba(255,255,255,.30);   /* primary cards */
  --card2:    rgba(255,255,255,.20);   /* secondary panels, left columns */
  --bd:       rgba(255,255,255,.55);   /* card borders */
  --bd2:      rgba(255,255,255,.15);   /* internal dividers */

  /* ── Shadows (tinted with palette color, NOT rgba(0,0,0,...)) ── */
  --sh:       0 8px 32px  rgba(47,65,74,.12);
  --sh-h:     0 16px 48px rgba(47,65,74,.20);

  /* ── Semantic severity colors (low-saturation, same family) ── */
  --ok:       #7DA59C;   --ok-bg:   rgba(125,165,156,.15);
  --warn:     #8A9E7A;   --warn-bg: rgba(138,158,122,.12);
  --bad:      #9E7A7A;   --bad-bg:  rgba(158,122,122,.12);

  /* ── Layout ── */
  --r:    24px;   /* larger than other palettes */
  --r2:   18px;
  --r3:   12px;
  --nav:  210px;
  --top:  48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  --e2:   cubic-bezier(.34,1.56,.64,1);

  /* ── Fonts ── */
  --ff:   'Montserrat', '幼圆', 'YouYuan', 'PingFang SC', sans-serif;
  --fm:   'Montserrat', '幼圆', 'YouYuan', monospace;
}

/* ── MANDATORY: fixed background — never changes while scrolling ── */
body {
  background: linear-gradient(160deg,
    #6a9aa6  0%,
    #8fb8b4  20%,
    #B2CECB  50%,
    #CEDFDE  72%,
    #DEEAEB  88%,
    #EBF3F3  100%) fixed;
  background-size: 100% 100%;
  font-family: var(--ff);
  color: var(--c-deep);
  -webkit-font-smoothing: antialiased;
}

/* ── Dark solid nav (contrast against light gradient) ── */
.sidebar {
  background: #2F414A;
  box-shadow: 2px 0 20px rgba(0,0,0,.15);
}
.topbar {
  background: #2F414A;
  box-shadow: 0 2px 12px rgba(0,0,0,.15);
}
/* Sidebar text overrides for dark bg */
.sb-brand   { color: rgba(222,234,235,.9); }
.sb-link    { color: rgba(255,255,255,.55); }
.sb-link:hover  { background: rgba(255,255,255,.08); color: rgba(255,255,255,.85); }
.sb-link.active { background: rgba(255,255,255,.15); color: #fff; font-weight: 700;
                  border-left-color: var(--c-soft); }

/* ── Glass cards ── */
.card {
  background: var(--card);
  backdrop-filter: blur(28px);
  -webkit-backdrop-filter: blur(28px);
  border: 1px solid var(--bd);
  border-radius: var(--r);
  padding: 22px 24px;
  box-shadow: var(--sh);
  transition: transform .2s var(--e2), box-shadow .2s;
}
.card:hover { transform: translateY(-3px); box-shadow: var(--sh-h); }

/* ── Sections: transparent — gradient shows through ── */
.section {
  background: transparent;
  border-bottom: 1px solid rgba(255,255,255,.12);
  padding: 32px 32px 36px;
}
.section:nth-child(even) { background: rgba(255,255,255,.06); }

/* ── KPI metric cards ── */
.ks-val {
  font-size: 36px; font-weight: 900;
  color: var(--c-deep); line-height: 1; letter-spacing: -.03em;
}
.ks-lbl {
  font-size: 9px; font-weight: 700; text-transform: uppercase;
  letter-spacing: 1.5px; color: rgba(47,65,74,.5);
}
.ks-u {
  font-size: 9px; font-weight: 700; letter-spacing: .5px;
  color: rgba(47,65,74,.45); margin: 0 6px 0 2px;
}

/* ── Section header ── */
.sh-tag {
  font-size: 10px; letter-spacing: 2px; text-transform: uppercase;
  color: rgba(255,255,255,.45); font-weight: 700; font-family: var(--ff);
}
.sh-title { font-size: 20px; font-weight: 900; color: var(--c-deep); letter-spacing: -.02em; }

/* ── Insight strips (glass variant) ── */
.ins {
  background: rgba(255,255,255,.28);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border: 1px solid rgba(255,255,255,.5);
  border-radius: var(--r2);
  padding: 14px 16px;
}
.ins.ok      { background: var(--ok-bg);   border-left: 3px solid var(--ok);   }
.ins.warn    { background: var(--warn-bg); border-left: 3px solid var(--warn); }
.ins.danger  { background: var(--bad-bg);  border-left: 3px solid var(--bad);  }

/* ── Cover ── */
#cover { background: transparent; }
.cv-h1 { color: #2F414A; font-weight: 900; letter-spacing: -.03em; }
.cv-h1 .kw { color: #3E5661; }
.cv-sub { color: rgba(47,65,74,.6); }
.cvs-n { color: #2F414A; font-weight: 900; }
.chip {
  background: rgba(255,255,255,.30);
  border: 1px solid rgba(47,65,74,.20);
  color: rgba(47,65,74,.55);
  backdrop-filter: blur(8px);
  border-radius: 100px;
}
```

**10-color palette:**
`#2F414A` `#3E5661` `#5C7E8C` `#7DA59C` `#9BB8BC` `#B2CECB` `#CEDFDE` `#DEEAEB` `#EBF3F3` `#ffffff`

**ECharts color sequence:**
```js
['#5C7E8C','#7DA59C','#9BB8BC','#3E5661','#8A9E7A','#9E7A7A','#7A8C9E','#B2CECB']
```

**Font load:**
```html
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
```

### Ice-Glass: do not forget

- [ ] `body` background uses `linear-gradient(...) fixed` as shorthand — NOT `background-attachment: fixed` split out
- [ ] Every `.card` has BOTH `backdrop-filter: blur(28px)` AND `-webkit-backdrop-filter: blur(28px)`
- [ ] No `overflow: hidden` on section parents (breaks backdrop-filter in Safari)
- [ ] `.section` backgrounds are `transparent` — no solid alternation
- [ ] Sidebar + topbar use solid `#2F414A`, text is white/light
- [ ] Chart colors use the low-saturation sequence — not ECharts default rainbow
- [ ] All shadows use `rgba(47,65,74,...)` — NOT `rgba(0,0,0,...)`
- [ ] `border-radius` unified as `var(--r)` = 24px

---

## Typography Scale (applies to all palettes)

| Use | Font variable | Size | Weight | Color |
|-----|--------------|------|--------|-------|
| Section title | `--fh` | 18px | 700 | `--text` / `--c-deep` |
| Card title | `--fh` | 14.5px | 700 | `--text` |
| Numeric KPI | `--fm` | 1.5–2.2rem | 700 | `--text` |
| Body | `--ff` | 13.5–14px | 400–500 | `--text` / `--muted` |
| Label (uppercase) | `--fm` | 9–11px | 700 | `--light`, letter-spacing 1.5px |
| Subtitle | `--ff` | 11.5–12px | 500 | `--light` / `--c-mid` |

Ice-Glass KPI values are 36px / weight 900 (larger than other palettes).

---

## Layout Rules

### Section backgrounds (palettes 1–3)
```css
.section:nth-child(odd)  { background: var(--bg); }
.section:nth-child(even) { background: var(--bg-alt); }
```
Section bg must be clearly distinct from `--card`. If they look similar, darken `--bg`.

### Section backgrounds (dark-glass, ice-glass)
Dark-glass: section bg derived from `--bg` / `--bg2` (near-black).
Ice-glass: section bg `transparent` — gradient always shows.

### Grid system
```css
.g2  { display: grid; grid-template-columns: 1fr 1fr;           gap: 13px; }
.g3  { display: grid; grid-template-columns: repeat(3, 1fr);    gap: 13px; }
.g55 { display: grid; grid-template-columns: 1fr 1fr;           gap: 13px; align-items: start; }
.g73 { display: grid; grid-template-columns: 7fr 3fr;           gap: 13px; align-items: start; }
```

### Chart layout rule (analysis mode)
```
✅ CORRECT:
[  Full-width chart card (100%)            ]
[  2×2 insight grid   |   data table       ]  ← g55

❌ WRONG:
[  Chart (60%)  |  Chart (40%)             ]  ← height mismatch, whitespace
```

---

## Severity Colors

### Palettes 1–3 (solid backgrounds)
| Level | Background | Text | Border |
|-------|-----------|------|--------|
| danger  | `rgba(208,152,106,.18)` | `#7A3800` | `var(--sd)` |
| warn    | `rgba(227,193,152,.25)` | `#5A4A00` | `var(--sw)` |
| neutral | `rgba(204,206,168,.20)` | `#3A3A20` | `var(--sn)` |
| ok      | `rgba(88,129,87,.12)`   | `#1A4020` | `var(--sok)` |

### Ice-Glass (glass backgrounds — low saturation)
| Level | Background | Border |
|-------|-----------|--------|
| ok      | `var(--ok-bg)`   = `rgba(125,165,156,.15)` | `var(--ok)`   = `#7DA59C` |
| warn    | `var(--warn-bg)` = `rgba(138,158,122,.12)` | `var(--warn)` = `#8A9E7A` |
| danger  | `var(--bad-bg)`  = `rgba(158,122,122,.12)` | `var(--bad)`  = `#9E7A7A` |

Apply to: insight strips, KPI accent bars, table cells, chart series colors.

---

## No-Data Cell Rule

Heatmap or map empty cells must use the **warm palette color**, never grey:

```css
/* Heatmap empty cell */
.ht-empty { background: #EDE8C0; color: var(--border); }

/* ECharts map no-data */
visualMap: { inRange: { color: ['#EDE8C0','#D0986A'] }, outOfRange: { color: '#EDE8C0' } }
```

For dark/glass palettes, use the section bg color for empty cells rather than grey.

---

## Spacing & Shared Tokens

```css
/* Sections */
.section { padding: 26px 32px 30px; }

/* Ice-Glass sections */
.section { padding: 32px 32px 36px; }

/* Shared radius shortcuts */
--r:  10px;  /* palettes 1–3, dark-glass: 12px */
--r:  24px;  /* ice-glass only */
```
