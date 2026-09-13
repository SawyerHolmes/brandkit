---
description: Check an existing HTML page against the brand kit and report what's off-brand or broken. Reports only; fixes when asked.
argument-hint: [path to an .html file, or a URL]
---

# /brand-check — audit a page against the brand

Target: **$ARGUMENTS** (an HTML file, or the current project if empty).

Load the `brand-craft` skill and read `~/.claude/brand/BRAND.md` (if it's missing, say to run `/brand-setup` first).

Go through the page and report every place it drifts from the kit, worst first, each with the line and the fix:

- **Colour** — any hex/`rgb()` not in the kit's tokens; any pair under 4.5:1 contrast; neutrals that are flat grey rather than the brand's biased ones.
- **Type** — fonts not in the kit; sizes off the scale; missing fallback stacks; missing `tabular-nums` on columns of figures.
- **Logo** — wrong version for the background, stretched or recoloured, below minimum size, clearspace crowded.
- **Each Hard rule** in the kit, checked one by one.
- **Quality floor** — 375px with no horizontal scroll, visible focus states, `prefers-reduced-motion`, 16px minimum on mobile inputs, alt/label on every meaningful control.

Separate **off-brand** (breaks the kit) from **polish** (would be nicer). Verify in the browser — screenshot before/after if you change anything. Do not change the file until asked; then fix the off-brand set and re-check.
