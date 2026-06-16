# rebrandit — Codex / GPT setup

Codex (and ChatGPT) can generate images **natively**, so rebrandit needs no API key or wallet
here — it just uses the built-in image tool.

## How to run

1. **Read `AGENT.md`** at the repo root — it's the complete, brand-agnostic playbook.
2. **Pick the brand:** the `BRAND` env var, else what the user named, else `sentient` (default).
   Read `brands/<brand>/brand.yaml` and its `context_file` if set.
3. **Image backend = native.** Per §1 of `AGENT.md`, since the host has built-in image
   generation, use it directly with the mode's prompt and the reference images in order. No
   `IMAGE_BACKEND`, no key.
4. Follow the §4 workflow: get input → pick mode → build prompt + ordered refs → generate →
   `strip_ai_provenance()` → show the result.

## Install

Drop this `AGENTS.md` (or its contents) where Codex reads project instructions, with the
rebrandit repo available so `AGENT.md`, `brands/`, and `docs/` resolve by relative path.

## Reference ordering reminder

The native image call must receive references in the order the mode requires (see the table in
`AGENT.md` §4, Step 3): input first, then logo and/or mascot. Always run `strip_ai_provenance()`
on the saved file before showing it.
