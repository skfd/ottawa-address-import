# ottawa-address-import

The **Ottawa city checkout** of the address-import family — city #13 in the
onboarding pass, scaffolded 2026-08-16 by the breadth-first loop (engine
`future-work/multi-city/onboarding-queue.md`). Status: **onboarding,
observer-leaning**. No proposal published, no uploads made; the config is a
first draft for conflation baseline runs.

The pipeline lives in the engine repo,
[`address-importer-friend`](https://github.com/skfd/address-importer-friend)
(see its README for setup). This repo carries only Ottawa's `config.toml`,
credentials (`.env.*`, gitignored, from the `.example` files), and —
locally, gitignored — `data/` with the OSM extract and `data/ottawa/tool.db`.

```bash
cd ../address-importer-friend
python run.py --city-dir ../ottawa-address-import
```

Source data: City of Ottawa municipal addresses via the sibling
[`ontario-address-changes`](https://github.com/skfd/ontario-address-changes)
tracker (`data/ottawa/ottawa.db`, 402,992 active rows / 349,142 civic at
snapshot 43, 2026-08-15 — the largest source after Toronto). The 2026-08-12
survey measured 15.3% missing with 82% of OSM addresses on building
polygons — a community-mapped city where the likely consumer is
**observer/QA**, not import; the survey's "by hand, no copy & paste or
import" mapper is owed a conversation before anything else, with Matthew
Darwin as the second contact.

Traits (details in config comments): stable key; ALL-CAPS abbreviated
streets; `FULLADDR` interleaves qualifier and unit; 18,002 QUALIFIER rows
whose letter belongs in the housenumber (a decision owed before any
import); ADDRTYPE splits MAIN/SUBORD 73/27; 10% units collapsed to civic;
tiles subdivide the 116 ONS Gen 3 neighbourhoods at 100.00% coverage.

Before anything visible: the etiquette conversation above, then (only if an
import is ever agreed) a wiki proposal per the
[OSM Import Guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines).

MIT licensed.
