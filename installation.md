# Installation

### 1. Drop the resource in

Place the `cas-shopv2` folder inside your resources directory, for example
`resources/[cas]/cas-shopv2`. The interface ships **pre-built** — no `npm` or build step.

### 2. Ensure it in `server.cfg`

Start it **after** your framework and inventory, so auto-detection and item artwork both work.

{% tabs %}
{% tab title="VORP" %}
```cfg
ensure vorp_core
ensure vorp_inventory
ensure cas-shopv2
```
{% endtab %}

{% tab title="RSG Core" %}
```cfg
ensure rsg-core
ensure rsg-inventory
ensure cas-shopv2
```
{% endtab %}
{% endtabs %}

### 3. Point it at your server

Open `config.lua` and set the essentials:

* `Config.Framework` and `Config.Inventory` — leave on `'auto'` unless you want to pin them.
* `Config.Currency.useGold` — turn gold off if your server is cash only.
* `Config.ItemImages.resource` — the inventory your item pictures live in (default `vorp_inventory`).

### 4. Place your counters

The shipped coordinates are Valentine / Emerald Ranch and are close, but every map build differs.

1. Set `Config.Debug = true`.
2. Restart and walk to where a counter should sit.
3. Run **`/shopcoords`** — it prints ready-to-paste, ground-corrected `ped` and `prompt` coordinates.
4. Paste them into the matching shop in `config/shops.lua`.
5. Set `Config.Debug = false` when you are done.

### 5. Restart

```
ensure cas-shopv2
```

Watch the console on start — the resource audits every item name in your shop config against your
inventory and lists any that are not registered. Resolve those before going live.
