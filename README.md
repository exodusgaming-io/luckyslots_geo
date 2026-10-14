# luckyslots_geo

The page Lucky Slots shows to visitors from restricted locations.

The Cloudflare worker `luckyslots-geo-blocker` (zone `luckyslots.us`, routes `luckyslots.us/*` and
`preview.luckyslots.us/*`) decides who is blocked and answers with HTTP 451 and a small wrapper page that
frames `https://exodusgaming-io.github.io/luckyslots_geo/geo.html?ref=<CF-Ray>`. Blocking rules and the
state list live in the worker, not here.

- `?ref=` — printed as "Reference" for support to quote; hidden when absent.
- `?regions=` — the restricted-region list, rendered as text in the "Restricted regions currently include:"
  panel; hidden when absent. The worker builds it from the same constant that does the blocking and sends it
  only for a regional block, so a visitor blocked by country is not shown a list of states.
- "Contact support" posts `openLiveChat` to the parent, which opens the Comm100 chat or falls back to
  `mailto:support@luckyslots.us`. Opened directly (not framed), the button is a plain mailto link.

Served by GitHub Pages from `main`. Design: Figma "Lucky Slots Asset Kit", frame "Area restricted 2" (node 2489:72410).
