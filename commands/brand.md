---
description: Build an interactive HTML page in the captured brand — palette, fonts, logos and rules applied, then verified in a browser.
argument-hint: [what you want the page to be]
---

# /brand — build an on-brand page

The page to build: **$ARGUMENTS**

Build a polished, interactive HTML page that looks unmistakably like this brand, then prove it works. Load the `brand-craft` skill (it ships with this plugin) and follow it.

## Step 0 — Load the brand (silent)

Read `~/.claude/brand/BRAND.md`. **If it doesn't exist, stop and say: "Run `/brand-setup` first so I know the brand."** Note the logo files in `~/.claude/brand/assets/`.

The brand kit is binding. Its Hard rules and colour tokens are not suggestions.

## Step 1 — Pin the page

If the request doesn't already say, ask briefly (one message, a few options):
- **What is it** — a landing page, a report, a calculator, a form, a dashboard, an invite?
- **The one thing** a visitor should do or take away.
- **Interactive how** — what should the visitor be able to *do* (filter, calculate, toggle, submit, step through)? "Interactive" is the point — decide the one interaction that earns its place.

Don't over-ask. If the request is clear, go.

## Step 2 — Build it from the kit

Per `brand-craft`:
- Every colour, size and radius is a **CSS custom property** taken from the kit — no raw hex in the markup.
- The brand's **fonts** with real fallback stacks; the **type scale** from the kit.
- The **logo** placed correctly — right version for the background, clearspace respected, never stretched or recoloured. Inline the SVG so it inherits colour and stays crisp.
- **Light and dark** authored together via tokens.
- The interaction actually works, in plain vanilla JS (no build step, no framework unless asked) so the file opens by double-clicking.
- The brand's **voice** in every word. Real copy, never lorem.

## Step 3 — Verify in a real browser (don't ask them to check)

Open the page and confirm it before handing it over:
- Screenshot it at **desktop and 375px mobile**, in **both light and dark**.
- Check the console for errors; exercise the interaction once and confirm it responds.
- Run the `brand-craft` pre-flight: contrast ≥4.5:1, visible focus states, logo rules kept, no raw hex, no emoji-as-icon, no horizontal scroll at 375px, `prefers-reduced-motion` respected.

Use `playwright-cli` if it's installed; otherwise use the built-in browser preview and screenshot. Fix anything wrong, re-shoot, then show the screenshots.

## Step 4 — Hand it over

Give the finished `.html` file (self-contained, double-click to open) and the screenshots. Say in one line what it does and what you assumed. If a page would be better with a real asset that doesn't exist yet (a photo, an icon), mark the slot clearly rather than faking it.
