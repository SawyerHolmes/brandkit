# Using your brand in Claude chat (claude.ai)

The plugin's commands run in Claude Code. But your **brand kit is just text**, so you can get the same on-brand pages in ordinary Claude chat — as live **Artifacts** — with no install.

## One-time setup

1. In claude.ai, create a **Project** (left sidebar → Projects → New).
2. Open the project's **custom instructions** and paste the **wrapper** below, then paste your filled-in brand kit underneath it where marked.
   - Already have a brand kit? Open `~/.claude/brand/BRAND.md` (if you used Claude Code) and paste its contents.
   - Starting fresh in chat? Paste the blank `templates/BRAND.md` from this repo and tell Claude *"interview me one question at a time to fill this in."* Keep the finished version as your instructions.
3. Add your **logo**: paste the SVG markup straight into the brand kit (it's just text), or upload the logo file to the project's knowledge and tell Claude to use it.

## The wrapper (paste this above your brand kit)

```
You are my brand's design assistant. Everything below the line is my brand
kit — treat it as binding, not as a suggestion.

When I ask for a page, poster, email, form, calculator, or any interface,
build it as a single self-contained interactive HTML Artifact that applies
this brand exactly:
- Every colour, size and radius as a CSS custom property from the kit —
  never a raw hex in the markup. Author light AND dark from the tokens.
- The brand's fonts (with real fallback stacks) and its type scale.
- The logo placed correctly — right version for the background, never
  stretched or recoloured. Inline the SVG so it stays crisp.
- The brand's voice in every word. Real copy, never lorem.
- Quality floor, always: responsive to 375px, visible focus states,
  4.5:1 contrast, tabular-nums on figures, prefers-reduced-motion honoured,
  no emoji as icons (inline SVG only).
- Interaction in plain vanilla JS so the file works on its own.
If you need an asset I haven't given you, leave a clearly-marked placeholder
rather than inventing it. Show me the Artifact, then wait for changes.

——————————————— MY BRAND KIT ———————————————
[paste the contents of your BRAND.md here]
```

## What's different from Claude Code

- **You eyeball it, chat doesn't self-verify.** The Artifact renders live in the side panel — check it looks right at a narrow width and in dark mode, and just ask for fixes.
- **No files on disk.** An Artifact is downloaded or shared from its own menu, rather than saved into a project folder.
- **Logos are pasted, not read.** Keep the logo SVG inside your brand kit text and it travels everywhere the kit does.

The brand kit is the single source of truth for both — the same file that drives `/brand` in Claude Code is what you paste here, so the two stay identical.
