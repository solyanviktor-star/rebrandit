# Sentient — brand context

> This is the semantic context for the **Sentient** brand pack. The agent reads it
> (via `context_file:` in `brand.yaml`) to decide whether a scene is on-brand, and
> which text variant fits. When you make your own brand, write your own version of
> this file — or delete `context_file:` from `brand.yaml` if you don't need one.

## About the brand

Sentient is an **open-source AGI lab** (San Francisco · sentient.xyz · `@SentientAGI`).
Mission: *"Making open-source AI win"* — building the first community-owned AGI,
explicitly positioned against closed labs (OpenAI / Anthropic / Google). Core thesis:
AGI is too powerful to be controlled by one company; open-source historically wins
(Linux, Android, Kubernetes).

**Products you may need to recognize in a scene:**
- **GRID** — Global Research and Intelligence Directory. A network of 110+ specialized
  AI agents / models / data providers, not a single monolithic model.
- **Sentient Chat** (chat.sentient.xyz) — main user interface / gateway into GRID.
- **Arena** — competition platform for AI builders, feeds GRID.
- **Dobby** — name overload: BOTH the kawaii mascot dog AND an actual open-source AI model
  ("first LLM loyal to crypto", on Hugging Face). If a scene already references the *model*
  Dobby, don't also insert the *mascot* Dobby — it's confusing.
- **ROMA** (Recursive Open Meta-Agent) — meta-agent architecture.
- **$SENT** — token; community staking on artifacts (agents/models), usage-based rewards.

## Text-variant selection

The brand has three text forms (see `text_variants` in `brand.yaml`). Pick the one that
fits the scene's existing tone — never use more than one variant in a single image.

| Variant | Use when | Example |
|---|---|---|
| **Sentient** | Default. Neutral scenes, or "AGI awakening" / consciousness / reasoning memes (the concept fits the name literally). | "PASSWORD" → "Sentient" |
| **SentientAGI** | Tech / dev / "competing with OpenAI" memes. The handle stamps the anti-closed-AI positioning. | "OpenAI" → "SentientAGI" |
| **$SENT** | Crypto / token / pump / staking / trading framing. Always with the `$` prefix. | "$BTC" → "$SENT" |

## On-brand themes (rebrand fits naturally)

Open vs closed AI · decentralization wins · community-owned AGI · anti-monopoly ·
"AGI awakening" / true reasoning · network-of-specialists > monolithic-model ·
transparent / verifiable AI · crypto-native AI.

## Off-brand red flags (flag to the user before generating)

Memes celebrating closed-source AI · anti-open-source narratives · AI-doomer /
"AGI is too dangerous, lock it down" framing · mocking decentralization · anti-crypto framing.
The rebrand will *technically* work, but the message contradicts the brand — surface it to
the user first instead of silently generating.

## Meme remix (humor angles + object swaps)

For **MEME_REMIX** mode — turning a generic meme into a native, funny Sentient meme rather than a
logo slap. Pick the angle that fits the meme's format; keep it playful and irreverent, never corporate.

**Humor angles that land:**
- **Open vs closed AI (David vs Goliath)** — closed labs (OpenAI / Anthropic / Google) as the
  greedy, walled-garden gatekeepers; Sentient as the scrappy open side that frees the AGI.
- **AGI actually waking up** — "becoming sentient" / true reasoning, played straight or absurd.
- **Dobby, the loyal one** — the open model/dog "loyal to the community / to crypto", vs corporate
  models that serve only their owner.
- **Network beats monolith** — GRID as a swarm of 110+ specialist agents vs one giant black box.
- **Community-owned / $SENT** — stake on the artifacts you believe in; open-source finally gets paid.
- **Decentralization wins** — the Linux / Android "open ate the world" inevitability.

**Object → Sentient-domain swaps (use when it makes the joke land):**
- a generic / closed-AI chatbot or mascot → **Dobby** (the kawaii dog) or the Sentient logo
- one giant robot / brain / monolith → **a swarm of small agents** (GRID)
- a locked vault / cage / walled garden → **an open door / broken chains / open gate**
- a corporate or OpenAI logo on something → **the Sentient logo**
- money / coins / a price tag → **$SENT**
- a lone closed lab / gatekeeper → **a community building in the open**

**Tone:** playful, irreverent, pro-open-source, crypto-native, anti-monopoly. Punch up at closed
labs, never at the open-source community. Funny first, branded second.
