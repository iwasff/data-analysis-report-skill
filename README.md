# Data Analysis Report Skill

Standalone Codex skill for building polished, self-contained HTML data reports, dashboards, and narrative slide-style reports.

## Install

In Codex, ask:

```text
Use skill-installer to install iwasff/data-analysis-report-skill path data-analysis-report
```

Or install from the GitHub URL:

```text
https://github.com/iwasff/data-analysis-report-skill/tree/main/data-analysis-report
```

Restart Codex after installing so the skill is loaded.

## What It Includes

- `analysis` mode for dashboard-style reports
- `narrative` mode for scroll-snap, slide-like reports
- Phase 0 style selector HTML for choosing the report style
- Five demo HTML reports
- Dimension references for mode, palette, UI style, typography, and motion
- Component and animation references

## Typical Prompt

```text
Use data-analysis-report in narrative mode to create an HTML report from this material.
If no Style Config is provided, first give me the Phase 0 selector and wait for
me to paste the generated Config before creating the report.
```

When no complete Style Config is provided, the skill must start with
`data-analysis-report/demos/phase0-style-selector.html`. The selector is the
canonical Phase 0 artifact; users pick the 5 style axes there, copy the generated
Config block, and paste it back to continue report generation.
