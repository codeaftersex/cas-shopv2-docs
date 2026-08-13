# Adding and editing shops

Every counter is one entry in **`config/shops.lua`** → `Config.Shops`. Copy an existing block,
change the fields, and you have a new store. Six are shipped: General Store, Gunsmith, Doctor,
Butcher, Stable and Fence.

### A shop, field by field

```lua
{
    id       = 'general_valentine',                 -- unique id
    label    = 'Valentine General Store',           -- title in the header
    short    = 'General Store',                      -- name in the store list
    sign     = 'kit_pouch_provisions',               -- header icon
    keeper   = 'Mrs. Abigail Doyle',                 -- shown as the proprietor
    town     = 'Valentine · New Hanover',
    tagline  = 'Dry goods, provisions & sundries',
    haggle   = 5,                                    -- % off the marked price at this counter
    hours    = { open = 7, close = 20 },             -- 24h in-game clock (open == close → always open)
    job      = nil,                                  -- e.g. 'shopkeeper' to lock the counter to a job

    ped      = { model = 'u_m_m_valgenstoreowner_01',
                 coords = vector4(-322.36, 803.12, 117.83, 87.5) },  -- x, y, z, heading
    prompt   = { coords = vector3(-322.36, 804.30, 117.83) },
    blip     = { sprite = 'blip_shop_store', name = 'General Store' },

    categories = {                                   -- the tabs this counter shows
        { id = 'provisions', label = 'Provisions' },
        { id = 'remedies',   label = 'Remedies' },
    },

    buys = { provisions = 0.35, remedies = 0.32 },   -- per-category sell rate (what it pays you)

    stock = {
        { name = 'bread', label = 'Bread', icon = 'consumable_bread_roll',
          cat = 'provisions', price = 0.35, stock = 40, weight = 0.25, rating = 2,
          desc = 'Baked this morning behind the counter.' },
        -- ...more items
    },
}
```

### The three rules to remember

{% hint style="danger" %}
**`name` must exist in your inventory.** Every `stock` item's `name` is checked against your
inventory's item database. An unregistered name makes the framework refuse the purchase with
*"you cannot carry that"*, however empty the satchel is. Weapons (`weapon_*`) are the exception —
they need no item row. The server prints an audit of every unknown name on start.
{% endhint %}

{% hint style="info" %}
**Coordinates drift between map builds.** Do not trust the shipped numbers. Set
`Config.Debug = true`, stand where the counter should be, and run **`/shopcoords`** to print
ground-corrected `ped` and `prompt` coordinates to paste here.
{% endhint %}

{% hint style="info" %}
**`icon` is only the picture.** It is any file in `web/public/tex/items/` (without `.png`), or the
matching inventory image. It never affects what the player actually receives — that is `name`.
{% endhint %}

### Selling

The **sell** catalogue is shared across every counter (`Config.SellCategories`). Each shop only
shows the categories it `buys` and only the goods the player is actually carrying. A butcher can
pay well for `game` and poorly for `valuables` simply through its `buys` rates.
