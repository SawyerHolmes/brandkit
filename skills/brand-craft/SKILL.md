---
name: brand-craft
description: Apply a captured brand kit to interactive HTML pages without producing generic, templated output. Use when building or reviewing a branded page, landing page, report, form, calculator, or dashboard that must match a company's palette, fonts, logos, and rules. Covers token discipline, logo handling, the accessibility floor, anti-generic construction, and browser verification.
---

# brand-craft

How to turn a brand kit (`~/.claude/brand/BRAND.md`) into an interactive HTML page that looks unmistakably like the brand and actually works. The kit is the source of truth; this skill is the method.

## The order of operations

1. **Read the kit first, build second.** Palette, type, logo rules, geometry, voice, hard rules. If a value the build needs isn't in the kit, add it to the kit, then use it — don't invent it inline.
2. **Pin the page** — what it is, the one thing the visitor should do, and the one interaction that earns its place.
3. **Build from tokens.** Then **verify in a browser.** Then hand over with proof.

## Token discipline (the thing that makes it consistent)

- Declare every brand value once as a CSS custom property in `:root`, and reference the tokens everywhere. **No raw hex, no raw px font sizes, in the markup.** This is what lets the whole page re-skin from one place and stay coherent.
- Author **light and dark together**: the bare `:root` holds the light palette; `@media (prefers-color-scheme: dark)` (guarded `:root:not([data-theme="light"])`) and `:root[data-theme="dark"]` redefine the *same token names*. Never define a colour only inside a dark block. `body` always sets an explicit background token — a transparent body borrows the host's colour and breaks.
- Stay on the kit's **type scale** and **spacing scale**. Arbitrary values are how a page starts to look unconsidered.
- `font-variant-numeric: tabular-nums` on any column or row of figures so digits line up.

## The logo — the most common place brands get abused

- Use the **right version for the background**: the primary logo on light grounds, the mono/reversed version on dark or busy ones. Never the light logo on a light ground.
- **Inline the SVG** into the markup so it inherits colour via `currentColor` and stays crisp at any size. Reference a raster only if no vector exists.
- **Never** stretch (keep aspect ratio), recolour outside the approved versions, add shadows/effects, or crowd it — honour the kit's clearspace and minimum size.
- Favicon: the square mark only, never the full wordmark shrunk down.

## The accessibility & quality floor (unannounced, always)

- Contrast **4.5:1** minimum for text against its background — measure it, don't eyeball it.
- Visible `:focus-visible` state on every interactive element; everything reachable by keyboard.
- Responsive to **375px** with no horizontal scroll; touch targets ≥44px; 16px minimum on mobile text inputs so iOS doesn't zoom.
- Honour `prefers-reduced-motion` — collapse animation to near-zero when asked.
- Every meaningful control has an accessible name; decorative SVG gets `aria-hidden="true"`.

## Don't produce generic AI-looking output

The tells to avoid unless the brand explicitly calls for them: a purple-to-blue gradient hero; Inter or Space Grotesk as the default face; emoji as section icons; a rounded card with a coloured left-stripe repeated everywhere; the same radius and shadow stamped on every block; three evenly-weighted feature cards; everything centered. The brand kit is the antidote — its specific palette, its real font, its actual voice are what make the page look like *this company* and no one else. Spend the boldness where the brand's personality lives; keep everything around it quiet.

## Interactive, and it opens by double-clicking

- Write the interaction in **plain vanilla JS** with no build step, so the `.html` file works when opened directly. Reach for a framework only if asked.
- What's interactive should look interactive (cursor, hover, focus, pressed states). A control says exactly what it does, and confirms when it's done.
- The page opens in a **realistic working state** — example data plainly marked as example, never an empty shell.

## Verify — never ask them to go and check

Open the finished page and confirm it yourself:
- Screenshot at **desktop and 375px**, in **both themes**.
- Console clear of errors; exercise the interaction once and confirm it responds.
- Walk the floor above and each **Hard rule** in the kit.

Use `playwright-cli` if present; otherwise the built-in browser preview. Fix what's wrong, re-shoot, then hand over the file plus the screenshots. If a page needs a real asset that doesn't exist (a photo, a custom icon), mark the slot — don't fake it.
