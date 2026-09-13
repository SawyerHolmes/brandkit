# Brandkit

Build good-looking, **interactive web pages that always match your brand** — your colours, your fonts, your logo — without needing to design anything yourself. You tell Claude your brand once; after that, every page it makes for you comes out on-brand and is checked in a real browser before you see it.

It runs inside **Claude Code**. (There's a note at the end on using the same brand in **Claude chat / claude.ai** too.)

---

## What you get

Three commands you type into Claude Code:

| Type this | What happens |
|---|---|
| `/brand-setup` | **Do this once.** Claude captures your brand — hand it your brand guidelines PDF, point it at your website, or just answer its questions. It saves everything to a brand kit. |
| `/brand make a … ` | Builds an interactive page in your brand. e.g. `/brand make a signup page for the autumn workshop`. |
| `/brand-check` | Point it at a page you already have; it tells you what's off-brand and offers to fix it. |

Your brand is saved at `~/.claude/brand/BRAND.md` — a plain file you (or Claude) can edit any time your brand changes.

---

## Install (about two minutes)

**The easy way:** open Claude Code inside this folder and say:

> "Install this plugin for me."

It'll walk you through the two commands below.

**Or do it yourself** — from inside this folder, in Claude Code:

```
/plugin marketplace add .
```
```
/plugin install brandkit@brandkit-marketplace
```

Then restart Claude Code (or run `/plugin` once) so it loads. That's it — the three commands are now available in every project.

---

## First run

1. Type `/brand-setup`.
2. Give it whatever you have — a brand guidelines PDF is best; a link to your website also works; or just answer the questions.
3. Drop your **logo files** into `~/.claude/brand/assets/` when it asks (an `.svg` is best — it stays sharp at any size).
4. It writes your brand kit and shows you a summary.

Now you're ready:

```
/brand make a one-page product announcement with a countdown to launch day
```

Claude builds it, opens it in a browser to check it, fixes anything wrong, and hands you a finished `.html` file you can double-click to open or send to anyone.

---

## Tips

- **Be specific about the interaction.** "Make a pricing page where you can toggle monthly/yearly" gives a better result than "make a pricing page".
- **The brand kit is yours to edit.** Open `~/.claude/brand/BRAND.md` and change a colour or rule any time — every future page picks it up.
- **It checks its own work.** You'll get screenshots (desktop + phone, light + dark). You never have to go and test it yourself.
- **It won't fake things it doesn't have.** If a page would be better with a real photo you haven't supplied, it leaves a clearly-marked slot rather than inventing one.

---

## Using your brand in Claude chat (claude.ai) too

The plugin itself only runs in Claude Code, but your **brand kit is just a text file**, so you can reuse it in Claude chat:

1. Open `~/.claude/brand/BRAND.md` and copy everything in it.
2. In claude.ai, make a **Project**, and paste the brand kit into the project's custom instructions.
3. Ask for an **Artifact**: "Build me an interactive HTML page for … following the brand kit above."

Chat can't verify in a browser or place your logo files automatically the way Claude Code does, but it will follow the same colours, fonts, and rules — so the two stay consistent.

---

## What's in this folder (for the curious)

```
brandkit/
├─ .claude-plugin/     plugin + marketplace manifest
├─ commands/           /brand-setup, /brand, /brand-check
├─ skills/brand-craft/ how Claude applies a brand to a page well
├─ hooks/              reminds Claude to use your brand on any page request
├─ templates/          the blank brand-kit structure /brand-setup fills in
└─ README.md           this file
```

Nothing here phones home or needs an account beyond Claude Code itself.

---

**No Claude Code? Use it in Claude chat instead** — see [CHAT.md](CHAT.md).
