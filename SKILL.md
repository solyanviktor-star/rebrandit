---
name: rebrandit
description: Rebrand any image/meme with a brand's logo, name, or mascot — natural integration, not a pasted watermark. Ships configured for Sentient; swap brands via a brand pack. Triggers — rebrand, rebrand this, rebrand meme, add logo, integrate logo, brand this image, sentient rebrand, ребренд, ребренд мем, добавь логотип, добавь маскота.
---

# rebrandit

This is the **rebrandit** skill. The full, brand-agnostic playbook is in
[`AGENT.md`](AGENT.md) next to this file. Follow it exactly.

## How to run

1. **Read [`AGENT.md`](AGENT.md)** (sibling of this file) — that is your complete instruction set.
2. **Pick the brand:** the `BRAND` env var, else what the user named, else `sentient` (default).
3. **Read `brands/<brand>/brand.yaml`** (and its `context_file` if set) and load the values.
4. **Image backend:** Claude Code has no native image generation, so use an external provider
   per [`docs/image-backends.md`](docs/image-backends.md). Read `IMAGE_BACKEND`
   (`degenai` | `gemini` | `fastgen` | `openai`); if unset, ask the user once and tell them
   which env var / key is needed. `degenai` (x402, USDC on Base, no signup) is the lowest-barrier option.
5. Follow the §4 workflow in `AGENT.md`: get input → pick mode → build prompt + ordered refs →
   generate → `strip_ai_provenance()` → show the result.

## Install

The **repo root is the skill** — `SKILL.md`, `AGENT.md`, `brands/`, and `docs/` must stay
together. Clone (or symlink) the repo so its root lands at `~/.claude/skills/rebrandit/`:

```bash
git clone https://github.com/<you>/rebrandit.git ~/.claude/skills/rebrandit
# or, if you already cloned it elsewhere, symlink it:
#   ln -s /path/to/rebrandit ~/.claude/skills/rebrandit
```

Claude Code then discovers `~/.claude/skills/rebrandit/SKILL.md` at the skill root and the
relative paths to `AGENT.md`, `brands/`, and `docs/` resolve.

## Note on paths

All paths in `AGENT.md` and the brand packs are **repo-relative** — run the agent with the
repo as the working directory (or with the repo available) so they resolve. Don't hard-code
absolute machine paths. Output goes to `output/` (git-ignored) by default — create it if it
doesn't exist — or wherever the user asks.
