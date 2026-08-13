# Troubleshooting

### "You cannot carry that" on a purchase, even with an empty satchel

The item's `name` in `config/shops.lua` is not registered in your inventory's item database. Add
the item there first, or fix the name. **Watch the console on start** — the resource audits every
shop item and lists the unknown ones by name. This is by far the most common issue.

### The shopkeeper is floating or sunk into the ground

The `Z` in the shop's `ped.coords` is off. Keep `Config.Peds.groundSnap = true` (the default) and
it is dropped onto the real floor. If the counter sits on something the ground probe cannot see (a
wagon bed, a custom MLO platform), set the `Z` by hand and turn `groundSnap` off for testing.

### No prompt appears at the counter

* Check the `prompt.coords` — use `/shopcoords` with `Config.Debug = true` to get the exact spot.
* Make sure you are inside `Config.Interaction.distance`.
* If it only shows a **Closed** prompt, the counter is outside its `hours`. Set
  `hours = { open = 0, close = 0 }` to keep it always open.

### The shelf shows the wrong pictures, or all fallback art

`Config.ItemImages` points at your inventory's image folder. Confirm `resource`, `path` and `ext`
match where your inventory stores item pictures (default `vorp_inventory` → `html/img/items` →
`.png`). Images are matched by **item name**, not by the `icon` field. Missing pictures fall back
to the bundled RDR2 art, which is expected.

### Framework or inventory not detected

Leave `Config.Framework` and `Config.Inventory` on `'auto'` and make sure this resource starts
**after** your framework and inventory in `server.cfg`. If auto-detection still misses, pin them
explicitly (`'vorp'` / `'rsg'`, `'vorp_inventory'` / `'rsg-inventory'`).

### Stock resets after a restart

That is by design — stock is held in memory and returns to its configured values on restart. There
is no database. Tune `Config.Stock` (`restockMinutes`, `restockPercent`) for live behaviour, or set
`Config.Stock.enabled = false` for bottomless shelves.

---

Still stuck? Reach us on the support channel listed on the product page.
