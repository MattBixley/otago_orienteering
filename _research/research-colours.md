# Otago / Dunedin Orienteering Club — Colour Scheme Extract

Source: https://www.dunedinorienteering.org/ (site title: **"Otago Orienteering"**), a Google Sites site.
Newer domain https://otagoorienteering.org/ does **not** resolve (DNS ENOTFOUND) as of 2026-07-15.

Colours were extracted from the raw HTML/CSS (163 KB) — Google Sites stores its theme as
`rgba(...)` values in inline `<style>` blocks (no `<meta name="theme-color">` was present).
All values below are converted to hex.

## Colours found (with usage)

| Hex | rgb / rgba | Where it is used |
|-----|-----------|------------------|
| **#007BBF** | rgba(0,123,191,1) | **Primary brand blue.** Header/banner background, button background, borders, heading/link text. 19+ occurrences. This is the dominant theme colour. |
| #007BBF @ 10% | rgba(0,123,191,0.10) | Tint fills / hover backgrounds derived from the brand blue |
| **#FFFFFF** | rgba(255,255,255,1) | Page background, button text, button borders (white text on blue buttons) |
| **#212121** | rgba(33,33,33,1) | Primary body text (near-black grey) |
| #0F0F0F | rgba(15,15,15,1) | Secondary/darker text (14 uses) |
| **#F0F0F0** | rgba(240,240,240,1) | Light grey section / block backgrounds |
| #3367D6 | rgba(51,103,214,1) | Google-default link blue in embedded content (12 uses as text colour) |
| #3C78D8 / #1155CC / #0000FF | — | Default link blues inside embedded Google Docs/Sheets content (not part of the site theme) |
| #000000 | — | Occasional pure-black (shadows, embedded content) |
| #F2A640 | — | Warm amber — only a colour param in an embedded Google Calendar URL, **not** a site theme colour |

Button style captured verbatim (class `.QmpIrf`):
`background:#007BBF; border:#FFFFFF; color:#FFFFFF; font-family:Bitter; 11pt` → blue button, white text and white outline.

### Fonts (bonus)
- **Bitter** (a slab-serif) — headings and buttons, the dominant font (55+ uses, `Bitter, Arial` fallback)
- **Montserrat** — secondary/accent text

## Element-by-element answer

- **Header / navigation bar:** background **#007BBF** (brand blue), text **#FFFFFF** (white).
- **Primary accent / brand colour:** **#007BBF** — a strong mid-tone blue. Used for buttons, links, headings and borders.
- **Secondary accent:** no distinct second brand colour; the site relies on tints of the blue (#007BBF @ 10%) plus a light grey **#F0F0F0** for section separation. Embedded Google content shows the default link blue #3367D6.
- **Page background:** **#FFFFFF** white; **body text #212121** (near-black), with #0F0F0F for some headings.
- **Logo:** the header logo/banner is served from googleusercontent.com (a raster image, so exact hex not in CSS). It sits on the blue #007BBF banner. Described as the club logo image; specific logo colours cannot be read from CSS — inspect the image directly if precise logo hex is needed.

## Overall feel

Clean, tidy **Google Sites** layout built around a single **medium blue (#007BBF)** on a **white** background with near-black text — an "aqua/ocean blue" theme rather than the classic green/orange orienteering palette. The slab-serif Bitter headings give it a slightly sporty, editorial character. Restrained and functional, minimal secondary colour.

## Recommended palette (CSS variables → hex)

```css
:root {
  /* Brand */
  --oo-primary:        #007BBF; /* brand blue — header, buttons, links, headings */
  --oo-primary-dark:   #005C90; /* suggested darker shade for hover/active (derived) */
  --oo-primary-tint:   #E6F2F8; /* ~10% brand blue for subtle fills/hover (derived) */

  /* Neutrals */
  --oo-bg:             #FFFFFF; /* page background */
  --oo-surface:        #F0F0F0; /* section / card background */
  --oo-text:           #212121; /* primary body text */
  --oo-text-strong:    #0F0F0F; /* headings / emphasis */
  --oo-on-primary:     #FFFFFF; /* text/icons on blue */

  /* Optional accent (use sparingly) */
  --oo-accent-amber:   #F2A640; /* warm amber seen in the calendar embed — optional highlight */

  /* Links inside embedded/default content */
  --oo-link:           #3367D6; /* default link blue (embeds) */
}
```

Notes:
- `--oo-primary-dark` (#005C90) and `--oo-primary-tint` (#E6F2F8) are derived suggestions, not lifted from the site — they give you hover/active and subtle-fill steps that match #007BBF.
- Fonts to match the current look: **Bitter** (headings/buttons) and **Montserrat** (secondary).
