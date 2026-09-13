# Brand kit — <BRAND NAME>

The single source of truth for this brand. Every page `/brand` builds is measured against it. Fill it once with `/brand-setup`; edit it by hand any time.

Lives at `~/.claude/brand/BRAND.md`. Logos live beside it in `~/.claude/brand/assets/`.

---

## 1. What this brand is

One or two lines: what the company does, who it's for, and the feeling its materials should give (e.g. "calm and precise", "warm and human", "bold and loud"). This sets the register for every page.

## 2. Colour

Every colour is a named token with a role. Pages use the token names, never raw hex. Authored for **light and dark** so pages work in both.

| Token | Light | Dark | Role |
|---|---|---|---|
| `--brand` | `#______` | `#______` | The primary brand colour |
| `--brand-ink` | `#______` | `#______` | Text/icon colour that sits ON the brand colour |
| `--ground` | `#______` | `#______` | Page background |
| `--surface` | `#______` | `#______` | Cards / raised areas |
| `--ink` | `#______` | `#______` | Primary text |
| `--ink-2` | `#______` | `#______` | Secondary text |
| `--hair` | `#______` | `#______` | Hairline borders / dividers |
| `--accent` | `#______` | `#______` | Secondary accent, if the brand has one |

- **Semantic colours** (success / warning / error) are separate from the brand colour and stay constant: success `#______`, warning `#______`, error `#______`.
- **Neutrals carry a slight warm or cool bias** toward the brand — never pure `#808080` grey.
- Every text/background pair must clear **4.5:1** contrast.

## 3. Type

Two families maximum — one for display, one for everything else. A mono is a permitted third for figures/code.

| Role | Family | Weights | Notes |
|---|---|---|---|
| Display / headings | `____________` | `___` | large sizes only |
| Body / UI | `____________` | `___` | the workhorse |
| Mono (optional) | `____________` | `___` | numbers, code |

- **Where the fonts come from:** Google Fonts link, or self-hosted files in `assets/fonts/`, or a `@font-face` data-URI. Always give a real system fallback stack.
- Type scale (stay on it): `____ / ____ / ____ / ____ / ____ px`.
- Casing rules: e.g. labels UPPERCASE tracked, headings sentence case.

## 4. Logo

Files in `~/.claude/brand/assets/`. **SVG preferred** so it stays crisp.

| File | Use it when |
|---|---|
| `logo.svg` | Primary, on light backgrounds |
| `logo-mono-light.svg` | On dark / photographic backgrounds |
| `logo-mark.svg` | Square icon / favicon use only |

- **Clearspace:** keep at least `____` of empty space around the logo (e.g. the height of its own mark).
- **Minimum size:** never render the wordmark below `____ px` tall.
- **Never:** stretch, recolour outside the approved versions, add effects, or place the light logo on a light background.

## 5. Geometry & motion

- **Radius:** one decision, held everywhere — `____ px` (plus any exceptions).
- **Spacing scale:** `4 / 8 / 12 / 16 / 24 / 32 / 48 / 64 px` (adjust to the brand).
- **Shadows:** used sparingly and warm/cool to match the ground, or not at all — state which.
- **Motion:** how much movement the brand wants (none / restrained / lively), and always honour `prefers-reduced-motion`.

## 6. Voice

A line or two on how the brand writes: e.g. "plain and direct, active voice, no jargon, British spelling." Applies to every word on the page.

## 7. Hard rules (never break)

A numbered list — the checkable bans that keep pages on-brand. Start here, add as you learn:

1. No emoji as icons — use inline SVG or the brand's own iconography.
2. No colour outside the tokens above; no raw hex in the markup.
3. No stretched, recoloured, or effect-laden logo.
4. Light and dark authored together — never one bolted on after.
5. Responsive to 375px, visible focus states, 4.5:1 contrast — always.
6. `font-variant-numeric: tabular-nums` on every column of figures.
7. _______________________________________________
