# luckyslots_geo

The page Lucky Slots shows to visitors from restricted locations.

The Cloudflare worker `luckyslots-geo-blocker` (zone `luckyslots.us`, routes `luckyslots.us/*` and
`preview.luckyslots.us/*`) decides who is blocked and answers with HTTP 451 and a small wrapper page that
frames `https://exodusgaming-io.github.io/luckyslots_geo/geo.html?ref=<CF-Ray>`. Blocking rules and the
state list live in the worker, not here.

- `?ref=` — printed as "Reference" for support to quote; hidden when absent.
- "Contact support" posts `openLiveChat` to the parent, which opens the Comm100 chat or falls back to
  `mailto:support@luckyslots.us`. Opened directly (not framed), the button is a plain mailto link.

Served by GitHub Pages from `main`. Design: Figma "Lucky Slots Asset Kit", frame "Area restricted 2" (node 2489:72410).
