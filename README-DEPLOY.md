# Liftwork.com — rebrand + agency pivot deploy (2026-09-14)

Full-site restyle to the new brand (charcoal `#14181D` ground, orange
`#EA5B2A` accent, cream sections) plus the agency pivot: the homepage now
leads with the full-service offer (Foundation / Promote / Engage, 15 tactic
cards) and reframes the AI platform as "The system" behind the agency.
New chevron-dot favicon (inline SVG, no favicon.ico needed). Same URLs, same
contact-form endpoint, same consent tooling; only index.html gained sections.

## What changed

| File | Change |
|---|---|
| `index.html` | Rewritten `<style>` block (new palette), new favicon + theme-color, meta/OG copy, hero kicker + lede, services intro line, footer tagline, wordmark dot. HTML structure, form JS, and consent hooks untouched. |
| `legal.css` | Retokened to dark palette; wordmark dot; footer/border adjustments. Serves `/privacy/` and `/data-deletion/`. |
| `consent.css` | Retokened to dark palette (banner + preferences dialog + GPC notice). |
| `privacy/index.html` | New favicon + `theme-color`; em dashes removed from copy. |
| `data-deletion/index.html` | New favicon + `theme-color`; em dashes removed. |
| `consent.js` | Two user-visible strings: em dashes replaced with colons. No logic changes. |
| `img/market-map.webp` | REPLACED: new dark-mode market map with the brand marker, blends into the page background. |

## Unchanged (do NOT overwrite if the server copies differ)

- `fonts/archivo-var.woff2` — unchanged.
- `img/*.webp` — unchanged EXCEPT `market-map.webp` (replaced, see above);
  the cream tiles/plates elsewhere are intentional.
- `/api/contact` backend — the form still posts there.

## Deploy mapping

New pages: /media-mix-modeling/, /attribution-incrementality/, and
/integrations/
(education/service pages; deploy the folders as-is). New images: `mmm-base.webp`, `geo-test.webp`, `dashboard-dark.webp`,
`conflict.webp`, `shield.webp`, `plug.webp`, `triangle.webp`, `refresh.webp`.
(`targeting.webp` and `reporting.webp` on the homepage were replaced by an
inline animated SVG and `dashboard-dark.webp`; `reporting.webp` is still
used on the analysis page.)

Note: the /services/ page has been REMOVED (delete it from the server if a
prior version deployed it); the Services & Channels nav item anchors to the
homepage section. New images since the original deploy include (`img/plan.webp`, `img/launch.webp`,
`img/optimize.webp`, `img/brands.webp`, `img/teams.webp`). The hero graphic is now an inline animated SVG (platform-integration
network with brand glyphs from the simple-icons open-source set); no image
file is involved. Images still used: `bars`, `plan`, `launch`, `optimize`,
`brands`, `teams`, `dashboard`, `approval`, `report`, `targeting`,
`reporting`, `audit`, `build`, `monitor`, `recommend`. No longer referenced
(safe to remove): `market-map`, `radar-full`, `radar-quadrant`, `panels`,
`gap-filled`, `review-ad`, `dashboard`, `approval`, `report` (the platform
section was removed).

The folder structure mirrors the live URLs exactly; copy the whole tree
to the web root as-is (fonts/ and img/ are unchanged except
`img/market-map.webp`).

Minimal deploy = the 7 changed files: `index.html`, `privacy/index.html`,
`data-deletion/index.html`, `legal.css`, `consent.css`, `consent.js`,
`img/market-map.webp`.

## Smoke test after deploy

1. `/` — dark charcoal page, "Liftwork •" wordmark, orange kicker text.
2. Favicon in the tab = orange dot with a dark chevron notch.
3. Cookie banner (fresh/incognito visit) renders dark with cream buttons.
4. `/privacy/` and `/data-deletion/` render dark and match the homepage.
5. Contact form still submits to `/api/contact`.
