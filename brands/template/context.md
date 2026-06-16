# YOUR_BRAND_NAME — brand context (template)

> OPTIONAL file. If you keep it, point `brand.yaml` at it with `context_file: context.md`.
> If you don't need brand-awareness, delete this file and the `context_file:` line.
>
> The agent reads this to decide whether a scene is on-brand and which text variant fits.
> Replace every section below with your brand's real details, then delete these quote lines.

## About the brand

One short paragraph: what your brand/project is, who it's for, the one-line mission, and
any handles or product names the agent should recognize if they show up in an image.

## Text-variant selection

If you defined more than one `text_variants` entry in `brand.yaml`, explain when to use each.

| Variant | Use when | Example |
|---|---|---|
| **YOUR_BRAND_NAME** | Default / neutral scenes. | "PASSWORD" → "YOUR_BRAND_NAME" |
| **YourBrandHandle** | Tech / product contexts (delete row if unused). | "OpenAI" → "YourBrandHandle" |
| **$TICKER** | Crypto / finance contexts (delete row if unused). | "$BTC" → "$TICKER" |

## On-brand themes (rebrand fits naturally)

List the topics/vibes where stamping your brand on a meme actually makes sense.

## Off-brand red flags (flag to the user before generating)

List the topics where the rebrand would technically work but contradict your brand — the
agent will surface these to the user instead of silently generating.
