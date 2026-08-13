# Config reference

Everything global lives in **`config.lua`**. The counters themselves live in
[`config/shops.lua`](shops.md). Every field is commented in-file; this is the quick tour.

### General

| Key | Default | Purpose |
| --- | --- | --- |
| `Config.Debug` | `false` | Enables `/shopcoords` and `/shop`, plus console output. |
| `Config.Language` | `'en'` | `'en'`, `'tr'` or `'es'`. Add your own in `locales/`. |
| `Config.Brand` | `'CAS'` | Shown in the interface footer. |
| `Config.Framework` | `'auto'` | `'auto'`, `'vorp'`, `'rsg'` or `'standalone'`. |
| `Config.Inventory` | `'auto'` | `'auto'`, `'vorp_inventory'`, `'rsg-inventory'` or `'none'`. |
| `Config.Notify` | `'auto'` | `'auto'`, `'framework'`, `'chat'` or `'none'`. |

### Money

`Config.Currency` sets the `symbol`, `decimals`, and how cash/gold map to your framework. Set
`useGold = false` to hide gold in the UI and never charge it.

### Interaction

`Config.Interaction` controls the native RDR2 hold prompt: the `key`, whether it is `hold` or a
single press, the `distance` it appears within, and `showClosed` for an out-of-hours prompt.

### Shopkeeper peds

`Config.Peds` streams keepers by distance. Notable fields:

* `enabled`, `invincible`, `frozen`, `blockEvents`, `turnToPlayer` (`turnCooldown`).
* `groundSnap` — drops the keeper onto the real floor height, so a slightly-off `Z` still lands.
* `outfit` — `'preset'` (the model's catalogue look) or `'random'`. Override per shop with `shop.ped.outfit`.

`Config.Performance` tunes the scan intervals, `spawnDistance`, `despawnBuffer` and `maxPedsAtOnce`.

### Item artwork

`Config.ItemImages` reads each item's picture straight from your inventory (`resource` + `path` +
`ext`), matched **by item name**. Anything missing falls back to the bundled RDR2 texture, so a
shelf is never blank. Set `enabled = false` to always use the bundled art.

### Blips & opening hours

* `Config.Blips` — per-shop sprites come from `config/shops.lua`; this sets the fallback and `scale`.
* `Config.Hours` — read the hour from `'client'` (the player's clock), `'realtime'` (server clock),
  or `'export'` wired to your own time resource.

### Stock, economy & security

| Block | What it controls |
| --- | --- |
| `Config.Stock` | Restock cadence (`restockMinutes` / `restockPercent`), whether sold goods return, the sell cap. Set `enabled = false` for bottomless shelves. |
| `Config.Economy` | `allowSelling`, `sellRateFallback`, `taxPercent`, rounding. |
| `Config.Security` | `maxDistance` at checkout, `maxLinesPerOrder`, `maxQtyPerLine`, `cooldownMs`, `logSuspicious`. All enforced server side. |
| `Config.Logs` | Console logging plus an optional Discord `webhook` for buys and sells. |
