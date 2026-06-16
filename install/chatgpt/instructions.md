# rebrandit — ChatGPT (Custom GPT) setup

ChatGPT generates images natively, so this is the no-key path. You can run rebrandit as a
Custom GPT by pasting the playbook into the GPT's instructions.

## Setup

1. Create a Custom GPT (or a Project) and enable the **image generation** tool.
2. Paste the contents of the repo's root **`AGENT.md`** into the GPT's *Instructions*.
3. Upload the active brand's assets and `brand.yaml` as **Knowledge** files so the GPT can read
   the brand name, color, logo/mascot descriptions, and text variants:
   - `brands/sentient/brand.yaml` + `brands/sentient/context.md`
   - `brands/sentient/assets/logo.png` (and `mascot.png` if used)
   - …or your own brand pack instead.
4. To ship a different brand, swap the Knowledge files for your brand pack (see
   [`docs/create-your-brand.md`](../../docs/create-your-brand.md)).

## Behavior

- **Image backend = native** (ChatGPT's built-in image tool). No API key, no wallet.
- The user sends an image and asks to rebrand it; follow the §3 mode selection and §5 prompt
  templates from `AGENT.md`, then produce the image.
- **Provenance (important):** the mandatory `strip_ai_provenance()` step (`AGENT.md` §6)
  **cannot run inside the Custom GPT UI** — there is no file system there. Images generated in
  the ChatGPT UI keep their "Made with AI" / C2PA provenance. Treat ChatGPT-UI output as a
  **draft**; for anything you'll actually post, run the rebrand through the **Codex** or
  **Claude Code** path (which strips provenance), or re-save the file through an external
  metadata stripper first.

## Tip

For users who'd rather not paste a long prompt, point them at the Codex or Claude Code install
instead — those read `AGENT.md` from the repo directly.
