# Image generation backends

rebrandit doesn't ship its own image model. It resolves a backend at runtime, in this order:

1. **Native host generation** — the assistant you're running in already generates images.
2. **An external provider** — for assistants that don't.

You only need to set up an external provider if your host has no native image generation.

---

## 1. Native host generation (no key needed)

Some coding assistants can generate/edit images out of the box. If you're running rebrandit
inside one of these, the agent uses it directly — no API key, no wallet, nothing to configure.

| Host | Native image generation? | What rebrandit does |
|---|---|---|
| **GPT / Codex / ChatGPT** | ✅ Yes | Uses the built-in image tool with the prompt + reference images. |
| **Claude Code** | ❌ No | Falls back to an external provider (below). |
| Others | Depends | Native if available, else external. |

> This is the whole point of rebrandit being portable: the *playbook* (modes, prompts,
> provenance stripping) is identical everywhere — only the generation call differs.

---

## 2. External providers (for hosts without native image gen)

Pick one and set `IMAGE_BACKEND` to its name (the agent will also just ask you once if it's unset).

### `degenai` — pay-per-call via x402, no signup ⚡ (lowest barrier)

**[deGenAi](https://x.com/deGenAiBase)** lets you call image/video models and **pay per
generation in USDC on Base** using the **x402** protocol — no account, no API-key approval, no
subscription. You fund a hot wallet with a few dollars and you're generating. For a stranger who
just cloned this repo, this is the fastest way to a working backend.

> 💡 You can grab the API straight from the author of deGenAi — see the announcement:
> **https://x.com/deGenAiBase/status/2055412781478776870** ([@deGenAiBase](https://x.com/deGenAiBase)).

**Setup**
1. Install the `degenai` CLI (install command + latest details in the tweet above / the
   [@deGenAiBase](https://x.com/deGenAiBase) profile).
2. Set `DEGENAI_PRIVATE_KEY` to a **hot wallet** private key, funded with ~$5–10 of **USDC on Base**.
   Use a throwaway wallet — never your main one.
3. Verify: `degenai init` (shows wallet address, USDC/ETH balance, and API reachability).

**Usage (what rebrandit calls)**
```bash
degenai generate -p "<prompt>" -i input.png -o output.png
```
- A reference image goes via `-i`. A rebrand needs at least the input scene **plus** the logo,
  so check `degenai generate --help` for how your CLI version passes more than one reference
  (and whether the chosen model accepts multiple). The `gpt-image-2` model (`-m gpt-image-2`)
  is the strongest pick for reference-driven edits and in-image typography.
- Live pricing: `degenai pricing` (source: `https://aibasegen.vercel.app/api/x402/pricing`).

**Pricing (indicative)**

| Model | Price | Notes |
|---|---|---|
| Nano Banana (Flow) | ~$0.005 | Cheapest; 1K; 16:9 / 9:16 / 4:3 / 3:4 |
| GPT Image 2 | ~$0.015 | Strong on typography & reference-driven edits |
| Nano Banana | ~$0.05 | Standard tier, up to 2K |
| Nano Pro | ~$0.15 | Top quality, up to 4K |
| Seedream | ~$0.10 | Creative-leaning |

### `gemini` — Google Gemini image model

The classic free-key option.
1. Get a key from **Google AI Studio** (https://aistudio.google.com/apikey).
2. Set `GEMINI_API_KEY` (e.g. in a local `.env` — never commit it).
3. rebrandit calls the Gemini image model with the input + brand reference images and the mode prompt.

Use the strongest available image-capable Gemini model for text replacement; lighter/flash
variants handle in-image typography worse.

---

## Keys & safety

- **Never commit keys or wallet private keys.** `.env`, `*.key`, and wallet files are
  git-ignored by this repo — keep it that way.
- Use a **dedicated hot wallet** for `DEGENAI_PRIVATE_KEY`, funded with only what you intend to spend.
- If no backend is configured, the agent tells you exactly which env var to set rather than failing silently.
