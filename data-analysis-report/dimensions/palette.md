# Dimension: Palette

Five complete color systems. Copy the `:root` block for the chosen palette and
replace the placeholder in the HTML. Do not mix colors across palettes.

---

## warm-green (Default)

**Character:** Warm amber on dark forest green. Earthy, professional, trustworthy.
**Best for:** Internal ops reports, return analysis, monthly reviews.
**Demo:** `demos/demo-A-analysis-solid.html`

```css
:root {
  /* Section backgrounds */
  --bg:         #7EA090;   /* odd sections  */
  --bg-alt:     #EDE8C0;   /* even sections */
  /* Cards — always lighter than sections */
  --card:       #F9F3DC;
  /* Structure */
  --dark:       #293D33;   /* sidebar, cover, topbar */
  --primary:    #588157;
  --tag:        #D6E8BC;   /* table headers */
  /* Text */
  --text:       #0F0F0D;
  --muted:      #3A4430;
  --light:      #5A7050;
  /* Borders */
  --border:     #A3B18A;
  --border-lt:  #C8D9A8;
  /* Severity */
  --sd:         #D0986A;   /* danger  */
  --sw:         #E3C198;   /* warning */
  --sn:         #CCCEA8;   /* neutral */
  --sok:        #A3B18A;   /* ok      */
  /* Shadows (use palette tint, not pure black) */
  --shadow:     0 2px 8px  rgba(41,61,51,.10);
  --shadow-h:   0 6px 20px rgba(41,61,51,.16);
  /* Shared */
  --r:    10px;
  --nav:  220px;
  --top:  48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  /* Fonts: set in typography axis */
  --ff: 'Noto Sans SC', sans-serif;
  --fh: 'Playfair Display', 'Noto Serif SC', serif;
  --fm: 'Space Mono', monospace;
}
```

**10-color palette** (only these — no ad-hoc hex):
`#D0986A` `#E3C198` `#F5EAC5` `#CCCEA8` `#A3B18A` `#7EA090` `#658C6E` `#588157` `#3A5A40` `#293D33`

**ECharts color sequence:**
```js
['#D0986A','#E3C198','#CCCEA8','#A3B18A','#7EA090','#658C6E','#588157','#3A5A40']
```

---

## ocean-blue

**Character:** Cool blue on near-black. Clean, corporate, data-forward.
**Best for:** External business reports, investor presentations, product analytics.
**Demo:** `demos/demo-B-analysis-ocean.html`

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
  --r:    10px;
  --nav:  240px;
  --top:  48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  --ff: 'Inter', sans-serif;
  --fnum: 'Montserrat', sans-serif;   /* for numeric values */
  --fm: 'Space Mono', monospace;
}
```

**ECharts color sequence:**
```js
['#906060','#C8A870','#8AAAC0','#3A8A6A','#2E6DA4','#4A7A96','#1A4A6A','#1A2F3A']
```

---

## slate-warm

**Character:** Amber accent on dark charcoal. Editorial, modern, brand-forward.
**Best for:** Brand analysis reports, narrative presentations, executive summaries.
**Demo:** `demos/demo-D-narrative-editorial.html`

```css
:root {
  --bg:         #EEEAE0;
  --bg2:        #E0DDD2;
  --bg3:        #F4F1E8;
  --dark:       #2A2A2A;
  --dark2:      #1E1E1E;
  --primary:    #7A6A4A;
  --warm:       #C17F4A;
  --warm2:      #D4AA70;
  --card:       #F4EEE0;   /* lighter than bg */
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
  --r:    10px;
  --nav:  220px;
  --top:  48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  --ff: 'Noto Serif SC', 'Noto Sans SC', serif;
  --fh: 'Playfair Display', 'Noto Serif SC', serif;
  --fm: 'Space Mono', monospace;
}
```

**ECharts color sequence:**
```js
['#C17F4A','#D4A860','#B0A888','#6A8A5A','#8A6A3A','#6A6A5A','#4A4A3A','#2A2A2A']
```

---

## dark-glass

**Character:** Smoky blue on near-black. Dramatic, immersive, technical.
**Best for:** Portfolio showcases, demo presentations, narrative tech reports.
**Demo:** `demos/demo-C-narrative-glass.html`

```css
:root {
  --bg:   #1a1f2e;
  --bg2:  #1f2438;
  /* Glass surfaces */
  --glass:  rgba(255,255,255,.055);
  --glassh: rgba(255,255,255,.090);
  --bd:     rgba(255,255,255,.090);
  --bdh:    rgba(255,255,255,.180);
  /* Accent colors (slate-blue / violet / emphasis) */
  --sl:   #7a9ab8;   /* slate blue — primary accent */
  --sl2:  #9bb4cb;
  --sl3:  rgba(122,154,184,.15);
  --vi:   #9b94b8;   /* violet */
  --vi2:  rgba(155,148,184,.15);
  --em:   #6ab4d4;   /* emphasis/highlight */
  --em2:  rgba(106,180,212,.15);
  /* Text */
  --t1:   #e2e8f4;   /* primary */
  --t2:   #8a94a8;   /* secondary */
  --t3:   #464f62;   /* muted */
  --shadow:   0 4px 20px rgba(0,0,0,.4);
  --shadow-h: 0 8px 40px rgba(0,0,0,.5);
  --r:   12px;
  --e1:  cubic-bezier(.16,1,.3,1);
  --e2:  cubic-bezier(.34,1.56,.64,1);
  --e3:  cubic-bezier(.4,0,.2,1);
  --ff: 'Inter', sans-serif;
  --fm: 'Space Mono', monospace;
}
body { background: var(--bg); color: var(--t1); }
```

**ECharts color sequence:**
```js
['#7a9ab8','#9bb4cb','#6ab4d4','#9b94b8','#5a7a98','#4a6a88','#3a5a78','#2a4a68']
```

**Card base (glass variant):**
```css
.card {
  background: var(--glass);
  border: 1px solid var(--bd);
  border-radius: var(--r);
  padding: 20px 22px;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
}
.card:hover { background: var(--glassh); border-color: var(--bdh); }
```

---

## ice-glass

**Character:** Cool teal fixed-gradient background + frosted glass cards.
Airy, luminous, brand-premium. Entire scroll happens over a static gradient.
**Best for:** Brand intelligence reports (CamPulse style), competitive analysis,
external showcase reports.
**Demo:** `demos/demo-E-analysis-iceglass.html`

### ⚠️ Architectural difference

Ice Glass is structurally different from the other four palettes:
- `body` uses `background: ... fixed` — gradient stays put while content scrolls
- `.card` uses `backdrop-filter: blur(28px)` — glass effect over the gradient
- `.section` is `background: transparent` — lets gradient show through
- Navigation: solid dark `#2F414A`, NOT semi-transparent
- Border radius: 24px (`--r`) everywhere — much larger than other palettes

```css
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&display=swap');

:root {
  /* Text */
  --c-deep:   #2F414A;   /* primary text, dark nav background */
  --c-mid:    #5C7E8C;   /* secondary text, labels */
  --c-soft:   #7DA59C;   /* status color, accents, timeline nodes */
  --c-muted:  #9BB8BC;   /* helper text */
  /* Glass cards */
  --card:     rgba(255,255,255,.30);
  --card2:    rgba(255,255,255,.20);   /* secondary panels */
  --bd:       rgba(255,255,255,.55);   /* card borders */
  --bd2:      rgba(255,255,255,.15);   /* internal dividers */
  /* Shadows (tinted with palette color, not pure black) */
  --sh:       0 8px 32px  rgba(47,65,74,.12);
  --sh-h:     0 16px 48px rgba(47,65,74,.20);
  /* Severity (low-saturation, same color family) */
  --ok:       #7DA59C;   --ok-bg:   rgba(125,165,156,.15);
  --warn:     #8A9E7A;   --warn-bg: rgba(138,158,122,.12);
  --bad:      #9E7A7A;   --bad-bg:  rgba(158,122,122,.12);
  /* Layout */
  --r:    24px;          /* ← larger than other palettes */
  --r2:   18px;
  --r3:   12px;
  --nav:  210px;
  --top:  48px;
  --e1:   cubic-bezier(.16,1,.3,1);
  --e2:   cubic-bezier(.34,1.56,.64,1);
  /* Fonts */
  --ff: 'Montserrat', '幼圆', 'YouYuan', 'PingFang SC', sans-serif;
  --fm: 'Montserrat', '幼圆', 'YouYuan', monospace;
}

/* ── Fixed gradient background (MANDATORY — body only) ── */
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
}

/* ── Dark solid navigation (contrast against light gradient) ── */
.sidebar { background: #2F414A; box-shadow: 2px 0 20px rgba(0,0,0,.15); }
.topbar  { background: #2F414A; box-shadow: 0 2px 12px rgba(0,0,0,.15); }

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

/* ── Transparent sections (gradient shows through) ── */
.section {
  background: transparent;
  border-bottom: 1px solid rgba(255,255,255,.12);
  padding: 32px 32px 36px;
}
.section:nth-child(even) { background: rgba(255,255,255,.06); }
```

**Font load:**
```html
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
```

**10-color palette:**
`#2F414A` `#3E5661` `#5C7E8C` `#7DA59C` `#9BB8BC` `#B2CECB` `#CEDFDE` `#DEEAEB` `#EBF3F3` `#ffffff`

**ECharts color sequence:**
```js
['#5C7E8C','#7DA59C','#9BB8BC','#3E5661','#8A9E7A','#9E7A7A','#7A8C9E','#B2CECB']
```

### Ice Glass checklist

- [ ] `body` uses `background: linear-gradient(...) fixed` — NOT `background-attachment: fixed` separately
- [ ] All `.card` have `backdrop-filter: blur(28px)` + `-webkit-backdrop-filter`
- [ ] `.section` backgrounds `transparent` — no solid color alternation
- [ ] Sidebar and topbar use solid `#2F414A`, white text
- [ ] Cover `background: transparent`, title `color: #2F414A`
- [ ] Chart colors use low-saturation sequence — NOT default ECharts rainbow
- [ ] Shadow color is `rgba(47,65,74,...)` — NOT `rgba(0,0,0,...)`
- [ ] `border-radius` uses `var(--r)` (24px) consistently
