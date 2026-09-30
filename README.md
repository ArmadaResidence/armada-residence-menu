# ARMADA RESIDENCE — Café & Restaurant · interactive web menu

Static site. Upload the whole folder to any web host (or open index.html over http://).

```
index.html                    the entire app (HTML + CSS + JS). Edit CONFIG at the top of the <script>.
assets/ARMADA_RESIDENCE_Logo_porcelain.png   official master artwork (untouched, resized only)
assets/ARMADA_Cafe_Restaurant_Menu_2026.pdf   the printable menu behind the "Download menu (PDF)" buttons — replace this file to update it
assets/icons/ + favicon.ico + site.webmanifest   favicon / home-screen icon = the approved AR monogram avatar (Porcelain on Oxblood)
.nojekyll                     keeps GitHub Pages from running Jekyll on the folder
assets/frames/<section>/desktop/frame_0000…0150.webp   the supplied 720×898 frames, untouched (highest quality available)
assets/frames/<section>/mobile/frame_0000…0150.webp    480×599 set for low-DPR phones (chosen automatically)
assets/frames/<section>/manifest.json                  the supplied manifests
data/menu_data.json           the menu as rendered (built from the catalog; approved flags, EN names)
data/catalog_source.json      catalog v14 — v13 plus the seven breakfast add-on prices from the printed breakfast page
data/catalog_original_v13.json  the catalog as originally supplied

Frame quality: the source videos (1288×1608, listed in assets/frames/index manifests) were not supplied — only
these 720×898 extractions. To regain real detail on large screens, re-extract 1080×1347 (or native) WebP frames
from the .mp4 files and drop them into a new assets/frames/<section>/large/ set (add it to FRAMES in index.html).
```

## Configure WhatsApp ordering
Open index.html, find `const CONFIG = {` near the top of the script and set:

    whatsappNumber: "966533798590",   // café WhatsApp from the printed menu (0533 798 590); international format, digits only

The cart opens https://wa.me/<number>?text=<encoded order>. "Copy order details" stays available as a fallback.

## Other switches in CONFIG
- `showPendingItems` — list unconfirmed items (no price, not orderable) or hide them.
- `vipOverride` — `null` follows the catalog (`availability_status`), `true`/`false` forces the VIP card.
- `sceneLength` / `snacksLength` — scroll distance per scene in viewport heights.

## Updating prices or items
Regenerate `index.html` from the catalog with the build script (or edit the `DATA` constant directly).
Only items with `review_status` approved/confirmed and a `price_sar` are marked `approved`; everything else is rendered as pending.
