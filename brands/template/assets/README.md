# Brand assets

Drop your brand's image files here, then reference them from `../brand.yaml`.

## Logo (required)

- **File:** `logo.png` (PNG with transparency is ideal; JPG works too)
- **Size:** anything from ~256px up is fine. Keep it under ~1 MB so uploads stay fast.
- **Content:** just the mark, on a clean/transparent background. The agent passes this as a
  visual reference, so a crisp, isolated logo gives the best integrations.

## Mascot (optional)

Only if you defined a `mascot:` block in `brand.yaml`.

- **File:** `mascot.png` — your character, ideally on a transparent background.
- **File (small):** `mascot-tiny.png` — an optional ~256px version. The full mascot can be
  large; the small one is used as a lighter reference payload to keep generations fast.
  If you don't make one, point `file_small` at the same file as `file`, or delete the line.

## Tips

- Match the `description:` text in `brand.yaml` to what's actually in these files — the model
  reads both the words and the picture.
- Don't commit secrets here. Only image assets belong in this folder.
- If your logo/mascot was AI-generated or edited, strip its provenance metadata before
  committing (the same thing rebrandit does to output — re-save from pixel data, or
  `exiftool -all= file.png`). Otherwise your shipped asset can carry a "Made with AI" tag.
