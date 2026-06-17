# rebrandit

**Rebrand any meme or image with a brand — natively, not as a pasted-on watermark.**

Give rebrandit a meme, screenshot, or photo, and it integrates a brand into the scene: stamps
the brand name over meme text, weaves the logo into a surface that already exists in the frame,
or drops the brand's mascot into the picture as a character. The result looks like the brand was
always part of the artwork.

It ships configured for **[Sentient](https://sentient.xyz)** out of the box, but the engine is
brand-agnostic — point it at your own logo and name and it becomes *your* rebrand agent.

## See it in action

**Default brand — Sentient.** A pixelated "BE KIND" poster: the Sentient logo is woven natively
into the starfield as pixel-art (LOGO_ADD mode), with the text and scene left untouched.

| Before | After — Sentient |
|:---:|:---:|
| <img src="examples/bekind-before.png" width="260" alt="original BE KIND poster"> | <img src="examples/bekind-after.png" width="260" alt="rebranded with the Sentient logo"> |

**Your own brand — CineMeta.** A generic meme rebranded: the flaming meteor becomes a film reel,
the sword a clapperboard, plus a camera, Oscar statuettes and a glowing "CineMeta" sign — while
the character and composition stay intact.

| Before | After — CineMeta |
|:---:|:---:|
| <img src="examples/input-10.jpg" width="320" alt="original meme"> | <img src="examples/output-10.png" width="320" alt="rebranded for CineMeta"> |

---

## Why it's portable

rebrandit is a **playbook** (`AGENT.md`) plus a **brand pack** (`brands/<brand>/`). The playbook
runs the same way in any AI coding assistant; only the image-generation step adapts to the host:

| You run it in… | Image generation | Setup |
|---|---|---|
| **GPT / Codex / ChatGPT** | Native built-in | None — it just uses the host's image tool |
| **Claude Code** (and others without native gen) | External provider | Set one API/x402 backend (below) |

So the same agent works whether your assistant can draw images itself or needs an external API.

## Quickstart

1. **Clone it**
   ```bash
   git clone https://github.com/solyanviktor-star/rebrandit.git && cd rebrandit
   ```
2. **Install for your assistant:**
   - **Claude Code** → the repo root is a ready-to-install skill ([`SKILL.md`](SKILL.md)).
     Clone it into your skills dir: `git clone https://github.com/solyanviktor-star/rebrandit.git ~/.claude/skills/rebrandit`.
   - **Codex / GPT** → [`install/codex/AGENTS.md`](install/codex/AGENTS.md)
   - **ChatGPT (Custom GPT)** → [`install/chatgpt/instructions.md`](install/chatgpt/instructions.md)
3. **Pick an image backend** — skip if your host generates images natively; otherwise see
   [Image backends](#image-backends).
4. **Use it:** give the agent an image (path or URL) and say *"rebrand this"*. It analyzes the
   scene, picks a mode, generates, strips AI provenance, and shows you the result.

## Image backends

If your assistant has **no** native image generation (e.g. Claude Code), set one backend.
Tell the agent which one with **`IMAGE_BACKEND=<name>`** (e.g. `IMAGE_BACKEND=degenai`) — or
just say it once in chat. Full guide: [`docs/image-backends.md`](docs/image-backends.md).

- **`degenai` — pay-per-call via x402, no signup** ⚡ *(lowest barrier)*
  Call image models and pay per generation in **USDC on Base** via the **x402** protocol —
  no account, no key approval. Fund a hot wallet with a few dollars and you're live.
  👉 **You can get the API straight from the author:**
  [x.com/deGenAiBase/status/2055412781478776870](https://x.com/deGenAiBase/status/2055412781478776870)
  · [@deGenAiBase](https://x.com/deGenAiBase)
- **`gemini`** — Google Gemini image model, free key from Google AI Studio (`GEMINI_API_KEY`).

> 🔒 Never commit keys or wallet private keys. `.env`, `*.key`, and wallet files are git-ignored.

## The modes

The agent works at two depths. **Integrate** — keep the scene, just add the brand (one brand
signal almost always beats two):

- **LOGO_ADD** — logo woven natively into the scene (never a corner watermark).
- **TEXT_REPLACE** — swap meme text for the brand name, keeping the exact font/style.
- **CHARACTER_REPLACE** — the mascot takes over the central character's role *(requires a mascot)*.
- **FULL_BRAND** — mascot + logo together (rare).

**Remix** — reinterpret the meme into a witty, on-brand joke:

- **MEME_REMIX** — rewrite the caption to a brand-domain punchline and swap objects for
  brand-themed equivalents, keeping the format and characters. Needs the brand's `context.md`
  humor/domain notes (the CineMeta example above is a MEME_REMIX). Funny first, branded second.

A brand with no mascot just uses LOGO_ADD, TEXT_REPLACE and MEME_REMIX — mascot modes auto-disable.

## Make it your own brand

```bash
cp -r brands/template brands/mybrand   # then edit brand.yaml + drop your logo in assets/
export BRAND=mybrand                    # shell-based hosts (Claude Code / Codex); or just tell the agent
```

`export BRAND=…` applies to shell-based hosts. In the ChatGPT Custom GPT path there's no shell —
you select a brand by uploading its brand pack as Knowledge (see
[`install/chatgpt/instructions.md`](install/chatgpt/instructions.md)).

Full walkthrough: [`docs/create-your-brand.md`](docs/create-your-brand.md). You edit one YAML
file and drop in your assets — no code changes.

## Repo layout

```
rebrandit/
├── SKILL.md                  # Claude Code skill entry (the repo root IS the skill)
├── AGENT.md                  # the brand-agnostic playbook (the engine)
├── brands/
│   ├── sentient/             # default brand pack (logo, Dobby mascot, $SENT vocab, context)
│   └── template/             # copy this to make your own brand
├── docs/
│   ├── image-backends.md     # native vs degenai/x402 vs gemini
│   └── create-your-brand.md  # step-by-step custom-brand guide
├── install/                  # wrappers for other hosts (codex · chatgpt)
├── LICENSE
└── README.md
```

## Brand assets & trademarks

The MIT [`LICENSE`](LICENSE) covers rebrandit's code and docs. The example **Sentient** logo and
**Dobby** mascot under `brands/sentient/` belong to their owners and are included only to make
the default build usable — they are **not** licensed to you under MIT. Respect each brand's
trademark and usage policy when rebranding.

## License

[MIT](LICENSE) for the code and docs.
