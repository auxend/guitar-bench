---
name: html-guide-boilerplate
description: >-
  Use this skill when asked to create or convert technical explanations, specs, runbooks, or cheat-sheets into beautiful, publication-grade, self-contained single-file HTML guides with dark-mode styling, responsive card grids, callouts, and inline SVG diagrams.
---

# HTML Guide Boilerplate Skill

This skill defines the design system, structural architecture, and asset boilerplate for producing standalone, offline-ready, high-aesthetic HTML technical guides and documentation (matching the style of `fender-offset-setup-guide.html` and `audio-plugin-guide.html`).

---

## 1. Design Principles & Aesthetic Rules

Every generated guide must follow these rules:

1. **Zero External Dependencies:**
   - No external fonts (Google Fonts), CDNs (Tailwind, Bootstrap), or third-party JS scripts.
   - Use high-quality system font stacks: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif` and modern monospace stacks.
   - The file must render flawlessly offline, in any browser, and in local file preview (`file://`).

2. **Dark-Mode Modern Workbench Theme:**
   - Backgrounds: Dark slate/obsidian (`#0b0f17`, `#131b26`, `#1a2332`).
   - Text: High-contrast white headers (`#ffffff`), soft slate body text (`#cbd5e1`, `#94a3b8`).
   - Accents: Neon cyan (`#38bdf8`), vibrant amber (`#fbbf24`), mint emerald (`#34d399`), coral rose (`#f43f5e`), electric purple (`#c084fc`).

3. **Information Density & Component Hierarchy:**
   - **Hero Header:** Gradient glow background, category badges, high-contrast title, and 1-2 sentence executive summary.
   - **Numbered Sections:** Clear `01`, `02`, `03` progression with bordered subheadings.
   - **Inline SVGs:** Clean, vectorized technical diagrams with monospace labels and annotated vectors instead of ascii art.
   - **Responsive Grids:** 2-column or 3-column auto-fit cards for comparing concepts (e.g. Jazzmaster vs Jaguar).
   - **Callout Containers:** Color-coded (cyan for tips, amber for warnings, rose for critical pitfalls).
   - **Golden Spec Tables:** Crisp, styled comparison tables with monospace `<code>` values.
   - **Ordered Process Steps:** Custom CSS circular counter badges for sequential step-by-step procedures.

---

## 2. Standard CSS Token System

Use this exact root variable block across all generated guides:

```css
:root {
  --bg-primary: #0b0f17;
  --bg-secondary: #131b26;
  --bg-card: #1a2332;
  --bg-card-hover: #222f42;
  --border-color: #273549;
  --border-accent: rgba(56, 189, 248, 0.35);
  --text-main: #f1f5f9;
  --text-muted: #94a3b8;
  --accent-cyan: #38bdf8;
  --accent-amber: #fbbf24;
  --accent-emerald: #34d399;
  --accent-rose: #f43f5e;
  --accent-purple: #c084fc;
  --tag-bg: rgba(56, 189, 248, 0.12);
  --font-mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
  --font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}
```

---

## 3. Standard Document Layout Template

When creating a new HTML guide, use the boilerplate template located at:
`.agents/skills/html-guide-boilerplate/template.html`

### Mandatory Sections:
1. **Header Block:** Title, badges, and scope.
2. **Core Architectural Concept / Physics:** The foundational "why" with an inline SVG diagram.
3. **Comparative Analysis:** Grid cards juxtaposing two sides (e.g., Problem vs Solution, Jazzmaster vs Jaguar, Engine vs View).
4. **Step-by-Step Runbook (T-R-A-I-N or Workflow):** Numbered sequence with actionable checks.
5. **Reference Spec Table:** Side-by-side numerical tolerances or configuration parameters.
6. **Diagnostic Troubleshooting:** Common failure symptoms and exact fixes.

---

## 4. Inline SVG Diagram Standards

To ensure SVG diagrams render cleanly across mobile and desktop:
- Use `viewBox="0 0 850 180"` with `width="100%"` and `height="100%"`.
- Set background container class to `.diagram-container` with subtle border and monospace header.
- Text elements must use `fill="#94a3b8"`, `font-family="var(--font-mono)"`, and `font-size="11px"`.
- Use contrasting stroke colors (`#38bdf8` for active paths, `#f43f5e` for failure/buzz zones, `#34d399` for correct paths).
