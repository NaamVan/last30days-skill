# South African Palette

A colour system drawn from the nine landscapes in the reference board (Desert, Nama Karoo, Grassland, Fynbos, Succulent Karoo, Indian Ocean Coastal Belt, Savanna, Forest, Fynbos super-bloom).

| File | Purpose |
|---|---|
| `tokens.json` | Primitive scales, semantic light/dark tokens, data-visualisation sets |
| `palette.css` | CSS custom properties. Light by default; dark via `prefers-color-scheme` or `data-theme="dark"` (data colours switch too) |
| `index.html` | Swatch sheet, chart preview, contrast and colour-blind checks |

## Roles

| Role | Source landscape | Key values |
|---|---|---|
| **Primary: Midnight Navy** | Indian Ocean at night | `navy-800 #002B57` (brand), `navy-950 #001431` (ink, dark-mode page), `navy-500 #2763B1` (ocean) |
| **Accent: Copper & Gold** | Nama Karoo rust, Savanna winter grass | `copper-500 #C17A35` (fills), `copper-700 #8A4A1E` (copper text), `copper-300 #E3B46A` (gold) |
| **Background: Sand & Off-white** | Coastal dunes | `sand-50 #FBF8F2` (page), `sand-100 #F4EDE1` (cards), `#FFFFFF` (raised) |
| **Neutral: Quartz & Sandstone** | Succulent Karoo quartz, Fynbos sandstone | `stone-100 #F0EFEC` (alt surface) to `stone-600 #5C5A55` (muted text) |
| **Data** | All biomes | Categorical, sequential and diverging sets below |

The navy keeps chroma high in its dark steps (hue about 281° in CIELAB LCh, chroma 28–48 from 600 to 950), so it reads as deep ocean ink rather than a greyed slate.

## Data visualisation

The landscape colours now form one set for charts. They are no longer general-purpose secondary colours.

**Categorical** (use in this order):

| # | Name | Biome | Light mode | Dark mode |
|---|---|---|---|---|
| 1 | Ocean | Indian Ocean coast | `#1C5790` | `#56A2F5` |
| 2 | Karoo Copper | Nama Karoo | `#BA6B3A` | `#F1974D` |
| 3 | Forest Jade | Afromontane forest | `#49875C` | `#5AB16B` |
| 4 | Protea | Fynbos super-bloom | `#D64D96` | `#C46687` |
| 5 | Surf Teal | Coastal belt surf | `#0896A4` | `#8ECBDC` |
| 6 | Savanna Gold | Savanna winter grass | `#AC8905` | `#F4CE57` |
| 7 | Red Clay | Savanna and desert soil | `#862C28` | `#CB624B` |
| 8 | Lithops Mauve | Succulent Karoo | `#9B7DC8` | `#C7A8ED` |

**Sequential (navy depth, low → high):** `#E5E9FA #C8D1EF #99AADB #6283C7 #2763B1 #044D94 #003B74 #002B57 #001E42`. In dark mode the order is reversed so high values are the brightest.

**Diverging (copper ← sand → navy):** `#8A4A1E #C17A35 #EFD2A2 #F4EDE1 #C8D1EF #2763B1 #002B57`

How the set was built: each colour starts from a biome hue. Lightness and chroma were then searched so that:
- every mark keeps at least 3:1 contrast against its page background (WCAG 1.4.11 for graphics)
- the smallest colour difference between any two series stays high in normal vision and in simulated deuteranopia, protanopia and tritanopia (Machado et al. 2009)

Rules:
- Use the colours in order. Stop at 6 series where you can, and group the rest as "Other" in `stone-400`.
- Label series directly or add markers. Never rely on colour alone.
- Keep status colours (success, warning, error, info) separate from data colours.

## Best practices applied

1. **60 / 30 / 10 balance.** Use about 60% sand and off-white grounds, 30% navy (ink, headers, primary buttons, nav) and no more than 10% copper or gold (calls to action, highlights, focus).
2. **Full tonal scales.** Primary, accent and neutrals each have a 50–950 ramp, so hover, pressed, subtle and border states come from the ramp instead of ad-hoc tints.
3. **Semantic tokens over raw hex.** Components reference `--color-*` and `--data-*`, never `--sa-navy-800` directly. Dark mode and future re-themes then swap values in one place.
4. **Warm neutrals.** The greys lean slightly warm (sandstone and quartz) so they sit comfortably beside sand and copper.
5. **Accessibility first (WCAG 2.2).** All text pairs meet 4.5:1 or more. Borders, focus rings and chart marks meet 3:1. Copper `#C17A35` is not a text colour on sand (3.25:1); use `accent-text` (`copper-700`) for copper words and navy ink for labels on copper buttons.
6. **Colour is never the only signal.** Pair status and data colours with icons, labels or markers.
7. **A designed dark mode, not an inversion.** Dark mode uses midnight-navy surfaces, sand text, a lighter copper and gold accent, and lifted data colours, all re-checked.
8. **Charts tested for colour blindness.** The data set's minimum separation is reported below for both themes.

## Contrast and separation results

### Light

| Foreground / Background | Use | Ratio | Result |
|---|---|---|---|
| `--color-text` / `--color-bg` | Body text | 17.31:1 | AAA |
| `--color-text` / `--color-surface` | Body text on card | 15.77:1 | AAA |
| `--color-text-muted` / `--color-bg` | Secondary text | 6.50:1 | AA |
| `--color-text-muted` / `--color-surface` | Secondary text on card | 5.92:1 | AA |
| `--color-text-on-primary` / `--color-primary` | Primary button label | 13.36:1 | AAA |
| `--color-text-on-accent` / `--color-accent` | Accent button label | 5.33:1 | AA |
| `--color-accent-text` / `--color-bg` | Copper text | 6.43:1 | AA |
| `--color-link` / `--color-bg` | Links | 7.94:1 | AAA |
| `--color-border` / `--color-bg` | Input borders (non-text) | 3.61:1 | AA |
| `--color-focus-ring` / `--color-bg` | Focus ring (non-text) | 3.25:1 | AA |
| `--color-success` / `--color-bg` | Success text | 5.96:1 | AA |
| `--color-warning` / `--color-bg` | Warning text | 5.39:1 | AA |
| `--color-error` / `--color-bg` | Error text | 6.35:1 | AA |
| `--color-info` / `--color-bg` | Info text | 5.65:1 | AA |
| `data-1` / `--color-bg` | Ocean chart mark (non-text) | 7.04:1 | AA |
| `data-2` / `--color-bg` | Karoo Copper chart mark (non-text) | 3.77:1 | AA |
| `data-3` / `--color-bg` | Forest Jade chart mark (non-text) | 4.04:1 | AA |
| `data-4` / `--color-bg` | Protea chart mark (non-text) | 3.70:1 | AA |
| `data-5` / `--color-bg` | Surf Teal chart mark (non-text) | 3.35:1 | AA |
| `data-6` / `--color-bg` | Savanna Gold chart mark (non-text) | 3.13:1 | AA |
| `data-7` / `--color-bg` | Red Clay chart mark (non-text) | 8.24:1 | AA |
| `data-8` / `--color-bg` | Lithops Mauve chart mark (non-text) | 3.22:1 | AA |

### Dark

| Foreground / Background | Use | Ratio | Result |
|---|---|---|---|
| `--color-text` / `--color-bg` | Body text | 15.77:1 | AAA |
| `--color-text` / `--color-surface` | Body text on card | 14.27:1 | AAA |
| `--color-text-muted` / `--color-bg` | Secondary text | 12.08:1 | AAA |
| `--color-text-muted` / `--color-surface` | Secondary text on card | 10.93:1 | AAA |
| `--color-text-on-primary` / `--color-primary` | Primary button label | 7.98:1 | AAA |
| `--color-text-on-accent` / `--color-accent` | Accent button label | 7.26:1 | AAA |
| `--color-accent-text` / `--color-bg` | Copper text | 9.61:1 | AAA |
| `--color-link` / `--color-bg` | Links | 7.98:1 | AAA |
| `--color-border` / `--color-bg` | Input borders (non-text) | 4.89:1 | AA |
| `--color-focus-ring` / `--color-bg` | Focus ring (non-text) | 9.61:1 | AA |
| `--color-success` / `--color-bg` | Success text | 8.35:1 | AAA |
| `--color-warning` / `--color-bg` | Warning text | 9.61:1 | AAA |
| `--color-error` / `--color-bg` | Error text | 7.21:1 | AAA |
| `--color-info` / `--color-bg` | Info text | 7.98:1 | AAA |
| `data-1` / `--color-bg` | Ocean chart mark (non-text) | 6.89:1 | AA |
| `data-2` / `--color-bg` | Karoo Copper chart mark (non-text) | 8.10:1 | AA |
| `data-3` / `--color-bg` | Forest Jade chart mark (non-text) | 6.93:1 | AA |
| `data-4` / `--color-bg` | Protea chart mark (non-text) | 4.89:1 | AA |
| `data-5` / `--color-bg` | Surf Teal chart mark (non-text) | 10.25:1 | AA |
| `data-6` / `--color-bg` | Savanna Gold chart mark (non-text) | 12.07:1 | AA |
| `data-7` / `--color-bg` | Red Clay chart mark (non-text) | 4.71:1 | AA |
| `data-8` / `--color-bg` | Lithops Mauve chart mark (non-text) | 8.96:1 | AA |

### Data colour separation (smallest ΔE between any two series)

| Vision | Light set | Dark set |
|---|---|---|
| Normal vision | 29.2 | 28.3 |
| Deuteranopia | 14.6 | 13.2 |
| Protanopia | 14.4 | 13.7 |
| Tritanopia | 13.6 | 14.8 |
