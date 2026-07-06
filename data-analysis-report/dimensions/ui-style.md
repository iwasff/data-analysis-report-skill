# Dimension: UI Style

Determines how cards and components look — independent of palette.
UI Style and Palette can be mixed freely (constraints noted below).

---

## solid (Default)

**Character:** Opaque fill cards, clearly lighter than section background.
Strong layer hierarchy. Best general-purpose choice.

**Works with:** warm-green, ocean-blue, slate-warm
**Avoid with:** dark-glass (use `glass` instead), ice-glass (use `glass-round` instead)

```css
/* .card */
.card {
  background: var(--card);
  border: 1px solid var(--border-lt);
  border-radius: var(--r);
  padding: 18px 20px;
  box-shadow: var(--shadow);
  transition: box-shadow .25s ease, transform .25s ease;
}
.card:hover {
  box-shadow: var(--shadow-h);
  transform: translateY(-2px);
}

/* Section alternation (REQUIRED — must be visually distinct from card) */
.section:nth-child(odd)  { background: var(--bg); }
.section:nth-child(even) { background: var(--bg-alt); }
```

**Contrast rule:** Section bg must always be clearly different from `--card`.
If they look similar, darken the section bg by 10–15%.

---

## glass

**Character:** Semi-transparent cards with `backdrop-filter: blur`. 
Cards appear to float above the background. Requires a dark or
colorful background to show the frosted effect.

**Works with:** dark-glass (ideal pairing), ice-glass (use `glass-round` for better fit)
**Avoid with:** warm-green, ocean-blue, slate-warm (light bg defeats the glass effect)

```css
/* .card */
.card {
  background: var(--glass);
  border: 1px solid var(--bd);
  border-radius: var(--r);
  padding: 20px 22px;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: var(--shadow);
  transition: background .2s, border-color .2s, transform .2s;
}
.card:hover {
  background: var(--glassh);
  border-color: var(--bdh);
  transform: translateY(-2px);
}

/* Sections transparent — background gradient/color shows through */
.section { background: transparent; border-bottom: 1px solid var(--bd); }
.section:nth-child(even) { background: rgba(255,255,255,.03); }
```

**Requirement:** `backdrop-filter` only works when the element has no
`overflow: hidden` ancestor in most browsers. Keep section/parent overflow as `visible`.

---

## minimal

**Character:** No fill, outline-only cards. Maximum whitespace and restraint.
Typography and data carry the visual weight — decoration is absent.

**Works with:** Any light palette (warm-green, ocean-blue, slate-warm). 
Less effective with dark-glass.

```css
/* .card */
.card {
  background: transparent;
  border: 1.5px solid var(--border);
  border-radius: var(--r);
  padding: 18px 20px;
  box-shadow: none;
  transition: border-color .2s;
}
.card:hover {
  border-color: var(--primary);
}

/* Sections: very subtle or no background */
.section:nth-child(odd)  { background: transparent; }
.section:nth-child(even) { background: rgba(0,0,0,.02); }
.section { border-bottom: 1px solid var(--border-lt); }
```

**Typography emphasis:** With minimal UI style, section titles and card labels
should be slightly bolder and rely more on whitespace for separation.

---

## editorial

**Character:** Left accent-bar + subtle border. Magazine/newspaper feel.
Typography-driven — the fonts do more work than the containers.

**Works best with:** slate-warm palette, narrative mode, serif typography.
**Also works with:** warm-green, ocean-blue for variety.

```css
/* .card — editorial style */
.card {
  background: var(--card);
  border: 1px solid var(--border-lt);
  border-left: 3px solid var(--primary);   /* ← signature left bar */
  border-radius: 0 var(--r) var(--r) 0;    /* ← only right corners rounded */
  padding: 16px 20px 16px 18px;
  box-shadow: var(--shadow);
  transition: border-left-color .2s, box-shadow .2s;
}
.card:hover {
  border-left-color: var(--sd);            /* accent bar changes on hover */
  box-shadow: var(--shadow-h);
}

/* Severity bar colors */
.card.danger  { border-left-color: var(--sd); }
.card.warning { border-left-color: var(--sw); }
.card.ok      { border-left-color: var(--sok); }

/* Section headers — editorial underline style */
.sec-title {
  padding-bottom: 10px;
  border-bottom: 2px solid var(--border);
  margin-bottom: 20px;
}

/* Section alternation */
.section:nth-child(odd)  { background: var(--bg); }
.section:nth-child(even) { background: var(--bg-alt); }
```

**Insight strips** (`editorial` mode variant):
```css
.ins {
  border-left: 3px solid var(--border);
  padding: 10px 14px;
  background: transparent;
  border-radius: 0 var(--r3) var(--r3) 0;
}
.ins.danger  { border-left-color: var(--sd);  background: rgba(193,127,74,.06); }
.ins.warning { border-left-color: var(--sw);  background: rgba(212,168,96,.05); }
.ins.ok      { border-left-color: var(--sok); background: rgba(106,138,90,.05); }
```

---

## glass-round

**Character:** High-transparency white glass + 24px corner radius.
The "CamPulse Ice Glass" signature style. Combines glass transparency with
large, friendly corner radius for a premium yet approachable look.

**Works with:** ice-glass palette (purpose-designed pairing)
**Avoid with:** other palettes (24px radius looks oversized on dark/editorial themes)

```css
/* .card */
.card {
  background: rgba(255,255,255,.30);
  backdrop-filter: blur(28px);
  -webkit-backdrop-filter: blur(28px);
  border: 1px solid rgba(255,255,255,.55);
  border-radius: 24px;                       /* ← signature large radius */
  padding: 22px 24px;
  box-shadow: 0 8px 32px rgba(47,65,74,.12);
  transition: transform .2s cubic-bezier(.34,1.56,.64,1), box-shadow .2s;
}
.card:hover {
  transform: translateY(-3px);
  box-shadow: 0 16px 48px rgba(47,65,74,.20);
}

/* Secondary card (left panels, sub-sections) */
.card2 {
  background: rgba(255,255,255,.20);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border: 1px solid rgba(255,255,255,.35);
  border-radius: 18px;
}

/* Sections transparent */
.section { background: transparent; border-bottom: 1px solid rgba(255,255,255,.12); }
.section:nth-child(even) { background: rgba(255,255,255,.06); }

/* Chip / badge elements */
.chip {
  background: rgba(255,255,255,.30);
  border: 1px solid rgba(47,65,74,.20);
  border-radius: 100px;
  backdrop-filter: blur(8px);
  padding: 4px 14px;
  font-size: 10px;
  color: rgba(47,65,74,.55);
}

/* Internal dividers */
.divider { height: 1px; background: rgba(255,255,255,.25); margin: 16px 0; }
```

**Note on `backdrop-filter`:** Do NOT add `overflow: hidden` to sections or
wrapper elements — it breaks `backdrop-filter` in Safari and some Chromium builds.
Use `border-radius` on the card itself only.
