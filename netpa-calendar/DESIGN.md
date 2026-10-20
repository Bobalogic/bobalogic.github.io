# netPA to Calendar: design system

Tokens live in the `:root` block at the top of `index.html`. Rules use tokens only; no hard-coded colours, font sizes or radii outside `:root`.

## Colour

| Token | Light | Use |
|---|---|---|
| `--paper` / `--card` | `#eef1fb` / `#fff` | Page ground / raised surfaces |
| `--ink` / `--soft` | `#141a3c` / `#5a6283` | Text / secondary text (≥ 5.3:1 on paper) |
| `--cobalt` | `#3150f5` | Primary action ("Show me how") |
| `--brand` (`--lime`) | `#c9f25b` | The bookmark itself (sticker, bookmarks bar). Nothing else. |

**Category colours.** Each one means the same thing everywhere on the page:

| Token | Colour | Means |
|---|---|---|
| `--cat-class` / `--cat-class-alt` | sun `#ffd23f` / peri `#b9c4ff` | A class |
| `--cat-exam` | pink `#ff9cbf` | An exam, midterm or presentation |
| `--cat-date` | mint `#7fe0c4` | An academic-calendar date (holiday, exam period, enrollment) |

Don't use pink or mint for anything that isn't an exam or an academic date. Step numbers are neutral (`--ink`) for that reason.

Dark mode redefines the neutrals and `--cobalt`. Category colours stay the same, and text on them always uses `--block-ink`.

## Type

Display: Syne (headings, step numbers). Body: Figtree.

| Token | Size | Use |
|---|---|---|
| `--t-h1` | clamp 2.3–4.1rem | Page title |
| `--t-h2` | clamp 1.5–2rem | Section titles |
| `--t-xl` | 1.6rem | Step numbers |
| `--t-lg` | 1.25rem | Lead text, list titles |
| `--t-base` | 17px | Body |
| `--t-sm` | 14px | Hints, secondary copy, buttons |
| `--t-xs` | 12px | Meta (event dates, tags) |
| `--t-micro` | 10px | Text inside drawn illustrations only (`aria-hidden`) |

## Shape

`--r-xs` 4 (grid cells) · `--r-sm` 8 (pills inside illustrations, event rows) · `--r-md` 14 (buttons, screens, disclosures) · `--r-lg` 22 (cards) · `--r-pill` (chips, toggles).

## Interaction

- Touch targets: `--tap` = 44px minimum for buttons, tabs and disclosure headers. The EN/PT toggle is 36px inside a 44px pill.
- Focus: 3px `--cobalt` outline, offset 3px.
- Motion: one load sequence (class blocks drop in, then the exam week). Disabled under `prefers-reduced-motion`.

## Components

- **Sticker**: the draggable bookmark. Brand lime, dashed ink border, slight tilt. It is the only draggable thing on the page.
- **Step card**: number badge, then copy, then a drawn "screen". Stacks to one column below 900px.
- **Screen**: a mock browser window. Decorative and `aria-hidden`; never put instructions only inside it.
- **Event row** (`.ev li`): a date tag filled with the category colour (text in `--block-ink`), then title and optional note. Rows are split by hairline `--rule` dividers; no coloured borders or stripes.
- **What-you-get card** (`.get`): plain card with a 1px `--rule` border; the category shows as an 18px square before the heading, the same swatch as the hero list.
- **Disclosure** (`details`): the whole header is the tap target. Used for the FAQ and the "copy the code" fallback.
