---
description: Capture this brand once — palette, fonts, logos, rules — into a reusable brand kit. Run this first.
argument-hint: [optional: a brand-guidelines PDF, a website URL, or nothing to be interviewed]
---

# /brand-setup — capture the brand

Goal: write a complete brand kit to `~/.claude/brand/BRAND.md` and save the logos to `~/.claude/brand/assets/`, so `/brand` can build on-brand pages every time. Run this once; edit the file by hand later whenever the brand changes.

Input, if any: **$ARGUMENTS**

## Step 0 — Set up the folder (silent)

Ensure `~/.claude/brand/` and `~/.claude/brand/assets/` exist. If a `~/.claude/brand/BRAND.md` is already there, say so and ask whether to update it or start over — never silently overwrite it.

Read the template at `${CLAUDE_PLUGIN_ROOT}/templates/BRAND.md` — that is the exact structure to produce.

## Step 1 — Get the brand in, by whatever route is easiest

Offer these, and use whichever the person has:

- **A brand guidelines document** (PDF, Word, image) — read it and pull out the palette hexes, fonts, logo rules, spacing, and voice. This is the richest source; prefer it.
- **A live website** — open it in the browser, screenshot it, and read the computed styles: sample the real colours, read the `font-family` stack, find the logo file. Confirm what you read rather than guessing.
- **An interview** — if there's no document or site, ask **one question at a time** (never a wall of questions): brand name → what it does and the feeling it should give → primary colour(s) → any dark-mode colours → fonts (and where they come from) → does it have a logo file → radius/spacing feel → voice → anything it must never look like.

Whichever route: **confirm the exact hex values, font names, and logo files** with the person before writing. A brand kit built on a guess is worse than none.

## Step 2 — Get the logos as files

Ask the person to drop logo files into `~/.claude/brand/assets/` (or hand them over in chat), **SVG preferred** so they stay crisp at any size. Name them plainly: `logo.svg` (primary), `logo-mono-light.svg` (for dark backgrounds), `logo-mark.svg` (square icon). If only a raster (PNG/JPG) exists, keep it but note in the kit that a vector version would be better. Never fabricate a logo — if none exists, record that and use the wordmark set in the brand font instead.

## Step 3 — Fill in the light AND dark palette

If the person only gave light-mode colours, derive a sensible dark set with them (don't just invert — keep contrast legible and the brand colour working on a dark ground) and show the pair for approval. Name every colour's bias (warm/cool) on purpose.

## Step 4 — Write the kit

Write `~/.claude/brand/BRAND.md` following the template exactly, with real values in every slot — no leftover blanks. Fill the **Hard rules** list with the specifics this brand needs. Then show the person a short summary (the palette, the fonts, the logos found) and tell them: it's saved, they can edit that file any time, and `/brand` will now use it.

Never invent a fact — a missing hex, an unknown font, an absent logo. Mark it clearly and ask, rather than filling it with a plausible-looking default.
