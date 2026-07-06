# Report Style System

Use this reference when building self-contained HTML reports.

## Style Config

Represent style decisions with five axes:

```text
Mode: analysis | narrative
Palette: warm-green | ocean-blue | slate-warm | dark-glass | ice-glass
UI Style: solid | glass | minimal | editorial | glass-round
Typography: serif | sans | mono-heavy | glass-round
Motion: subtle | standard | expressive
```

Default when unspecified:

```text
Mode: analysis
Palette: warm-green
UI Style: solid
Typography: serif
Motion: standard
```

## Palette Notes

- `warm-green`: grounded business report, suitable for operations and user insight.
- `ocean-blue`: clean analytical dashboard.
- `slate-warm`: editorial insight report with warm accent.
- `dark-glass`: high-impact narrative or presentation style.
- `ice-glass`: translucent modern analytical report.

## Report Invariants

- Single HTML file.
- Inline CSS and JS.
- CDN only for fonts and ECharts.
- No build step.
- Chart containers must have stable dimensions.
- Every ECharts chart must resize on `window.resize`.
- Important KPIs must show source fields or calculation context.
- Dense operational reports should avoid oversized landing-page hero treatment.

## Accessibility and Fit

- Keep contrast strong.
- Avoid text overlap on mobile and desktop.
- Do not scale body text purely by viewport width.
- Use responsive grids, `minmax`, and chart aspect constraints.
