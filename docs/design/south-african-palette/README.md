# South African Palette

A colour system drawn from the nine landscapes in the reference board (Desert, Nama Karoo, Grassland, Fynbos, Succulent Karoo, Indian Ocean Coastal Belt, Savanna, Forest, Fynbos super-bloom).

| File | Purpose |
|---|---|
| `tokens.json` | Primitive scales, secondary biome colours, semantic light/dark tokens, chart order |
| `palette.css` | CSS custom properties; light by default, dark via `prefers-color-scheme` or `data-theme="dark"` |
| `index.html` | Swatch sheet, contrast tables and a live UI sample |

## Roles

| Role | Source landscape | Key values |
|---|---|---|
| **Primary: Midnight Navy** | Indian Ocean deep water | `navy-800 #13294B` (brand), `navy-950 #0B1A2E` (ink), `navy-500 #2C5A8F` (ocean) |
| **Accent: Copper & Gold** | Nama Karoo rust, Savanna winter grass | `copper-500 #C17A35` (fills), `copper-700 #8A4A1E` (copper text), `copper-300 #E3B46A` (gold) |
| **Background: Sand & Off-white** | Coastal dunes | `sand-50 #FBF8F2` (page), `sand-100 #F4EDE1` (cards), `#FFFFFF` (raised) |
| **Neutral: Quartz & Sandstone** | Succulent Karoo quartz, Fynbos sandstone | `stone-100 #F0EFEC` (alt surface) … `stone-600 #5C5A55` (muted text) |
| **Secondary: Biome hues** | All biomes | Red Sand `#B4462B`, Red Clay `#9C3B22`, Protea `#B83A78`, Fynbos Sage `#7E8F7E`, Emerald `#1E5A3F`, Jade `#3E8A6A`, New-Growth `#6F8F3A`, Surf Teal `#2A7F8C`, Lithops Mauve `#7D6A8C`, Charcoal `#2E2C2A` |

## Best practices applied

1. **60 / 30 / 10 balance.** Use about 60% sand and off-white grounds, 30% navy (ink, headers, primary buttons, nav) and no more than 10% copper or gold (CTAs, highlights, focus). Secondary biome hues are for tags, illustration, charts and image overlays. They should never compete with the navy-and-copper pairing.
2. **Full tonal scales.** Primary, accent and neutrals each have a 50–950 ramp, so hover, pressed, subtle and border states come from the ramp rather than from ad-hoc tints.
3. **Semantic tokens over raw hex.** Components reference `--color-primary`, `--color-surface` and similar tokens, never `--sa-navy-800` directly. This lets dark mode and future re-themes swap values in one place.
4. **Warm neutrals.** The greys lean slightly warm (sandstone/quartz) so they sit comfortably beside sand and copper, avoiding a cold blue-grey clash.
5. **Accessibility first (WCAG 2.2).** Every semantic text pair meets AA at 4.5:1 or better, and UI borders and the focus ring meet the 3:1 non-text requirement. Results are in the tables below.
   - Copper `#C17A35` is **not** a text colour on sand (3.25:1). Use `accent-text` (`copper-700`) for copper words, and navy ink (5.08:1) for labels on copper buttons.
   - The light secondary hues (Fynbos Sage, Jade, New-Growth, Surf Teal) fall below 4.5:1 against sand. Use them as fills with navy or white text checked per use, or as large graphics only.
6. **Colour is never the only signal.** Pair status colours with icons or text. Success uses forest green, warning uses gold-brown, error uses red clay and info uses ocean blue, so they read as distinct even in greyscale.
7. **Designed dark mode, not inverted.** Dark mode uses midnight navy surfaces, sand text and a lighter copper/gold accent, all re-checked for contrast.
8. **Chart order.** The categorical series starts with navy and copper, then alternates hue families (green, pink, teal, gold, red, mauve) to maximise separation between neighbouring series.

## Contrast results

### Light

| Foreground / Background | Use | Ratio | Result |
|---|---|---|---|
| `text` / `bg` | Body text | 16.49:1 | AAA |
| `text` / `surface` | Body text on card | 15.02:1 | AAA |
| `text-muted` / `bg` | Secondary text | 6.50:1 | AA |
| `text-muted` / `surface` | Secondary text on card | 5.92:1 | AA |
| `text-on-primary` / `primary` | Primary button label | 13.70:1 | AAA |
| `text-on-accent` / `accent` | Accent button label | 5.08:1 | AA |
| `accent-text` / `bg` | Copper text / eyebrow | 6.43:1 | AA |
| `link` / `bg` | Links | 9.04:1 | AAA |
| `border` / `bg` | Input borders / UI (non-text 3:1) | 3.61:1 | AA |
| `focus-ring` / `bg` | Focus ring (non-text 3:1) | 3.25:1 | AA |
| `success` / `bg` | Success text | 5.96:1 | AA |
| `warning` / `bg` | Warning text | 5.39:1 | AA |
| `error` / `bg` | Error text | 6.35:1 | AA |
| `info` / `bg` | Info text | 6.68:1 | AA |

### Dark

| Foreground / Background | Use | Ratio | Result |
|---|---|---|---|
| `text` / `bg` | Body text | 15.02:1 | AAA |
| `text` / `surface` | Body text on card | 13.83:1 | AAA |
| `text-muted` / `bg` | Secondary text | 11.05:1 | AAA |
| `text-muted` / `surface` | Secondary text on card | 10.17:1 | AAA |
| `text-on-primary` / `primary` | Primary button label | 7.12:1 | AAA |
| `text-on-accent` / `accent` | Accent button label | 6.91:1 | AA |
| `accent-text` / `bg` | Copper text / eyebrow | 9.16:1 | AAA |
| `link` / `bg` | Links | 7.12:1 | AAA |
| `border` / `bg` | Input borders / UI (non-text 3:1) | 4.24:1 | AA |
| `focus-ring` / `bg` | Focus ring (non-text 3:1) | 9.16:1 | AAA |
| `success` / `bg` | Success text | 7.95:1 | AAA |
| `warning` / `bg` | Warning text | 9.16:1 | AAA |
| `error` / `bg` | Error text | 6.87:1 | AA |
| `info` / `bg` | Info text | 7.12:1 | AAA |
