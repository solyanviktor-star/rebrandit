# Make rebrandit your own brand

rebrandit ships configured for **Sentient**, but the engine (`AGENT.md`) is brand-agnostic.
To rebrand memes/images with *your* logo and name, you just create a new brand pack — no code
to touch.

> **Where things live:** `brands/` sits at the repo root. Every path in `brand.yaml` is relative
> to its own `brands/<brand>/` folder, and the agent must run with the repo available — run it
> from the repo root, or install the skill (`SKILL.md`, `AGENT.md`, `brands/`, `docs/` together)
> — so the paths resolve.

## 1. Copy the template

```bash
cp -r brands/template brands/mybrand
```

(`mybrand` = a short lowercase folder name for your brand.)

## 2. Add your assets

Put your image files in `brands/mybrand/assets/`:
- `logo.png` — your logo, ideally on a transparent background, under ~1 MB.
- `mascot.png` — *optional*, only if your brand has a character mascot.
- `mascot-tiny.png` — *optional* small version of the mascot for faster uploads.

See `brands/template/assets/README.md` for size/format tips.

## 3. Edit `brands/mybrand/brand.yaml`

Fill in:
- `name` — your brand's display name.
- `text_variants.default` — the text the agent stamps over meme captions. Add `technical`
  and/or `ticker` only if you have those forms (otherwise delete those lines).
- `color` — your primary hex color.
- `logo.file` + `logo.description` — point to your file and **describe it in words** (shape,
  colors, letters). The model reads both the words and the picture.
- `mascot:` — the template ships this block **commented out**. Uncomment and fill it in if you
  have a mascot, or leave it commented / delete it if you don't. With no mascot, the agent uses
  only LOGO_ADD and TEXT_REPLACE (mascot modes auto-disable).
- `output_prefix` — prefix for saved filenames.

## 4. (Optional) Write `brands/mybrand/context.md`

If you want the agent to be brand-aware — to know which scenes are on-brand, when to flag an
off-brand meme, and which text variant to use — fill in `context.md` and **uncomment** the
`context_file: context.md` line in `brand.yaml` (it ships commented out). If you don't need it,
delete the file and leave that line commented.

Fill in the **Meme remix** section (humor angles + object→domain swaps) if you want the agent to
do *creative meme remixes* for your brand — rewriting captions to brand-domain jokes and swapping
objects for brand-themed equivalents (the **MEME_REMIX** mode), not just integrating the logo.
Without it, the agent stays conservative (LOGO_ADD / TEXT_REPLACE only).

## 5. Run with your brand

Tell the agent to use your brand, or set the env var:

```bash
# Claude Code / shell-based hosts
export BRAND=mybrand
```

…then point it at an image and ask for a rebrand. That's it — the same five modes, prompts, and
provenance stripping now run with your logo, your name, and (optionally) your mascot.

## What a brand without a mascot looks like

Plenty of brands have only a logo. That's fully supported: delete the `mascot:` block in
`brand.yaml`, and rebrandit will only ever do **LOGO_ADD** (native logo integration) and
**TEXT_REPLACE** (swap meme text for your brand name). No mascot cameos, no character swaps.

## Picking an image backend

The brand pack defines *what* gets stamped; the **image backend** defines *how* it's generated.
Those are independent — see [`image-backends.md`](image-backends.md). If you're in GPT/Codex,
native generation is used automatically; in Claude Code, set up `degenai` (x402, no signup) or
`gemini`.
