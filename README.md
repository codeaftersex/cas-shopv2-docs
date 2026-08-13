---
description: A complete, server-authoritative shop system for RedM, built from real RDR2 UI art.
---

# CAS Shops & Stores

**CAS Shops & Stores** replaces the usual list-menu shop with a full merchant interface: a
browsable shelf, a working satchel, an order basket, and a bill of sale to confirm against.
Every counter is staffed by a shopkeeper who is streamed in as the player approaches, dressed
correctly, placed on the floor, and turned to face whoever steps up to the counter.

Six trading counters are configured and ready on install. Adding your own is a matter of editing
one file.

{% hint style="info" %}
Nothing the interface reports is trusted. Prices, discounts, stock, opening hours and carrying
capacity are all recalculated on the **server** before a single coin changes hands.
{% endhint %}

### Highlights

* **Buy and sell** on one screen, with category tabs, live search, sorting and an editable order basket.
* **Bill of sale** confirmation with subtotal, discount, tax and total payable.
* **Six staffed counters** out of the box: General Store, Gunsmith, Doctor, Butcher, Stable and Fence.
* **Real RDR2 look** — genuine interface textures and the official RDR typefaces, no web chrome.
* **Item artwork** pulled straight from your inventory, with a bundled fallback so a shelf is never blank.
* **Living economy** — per-shop haggle discounts, per-category sell rates, global tax, cash and gold.
* **Stock & restock** — per-item stock, scheduled restock ticks, resold goods returning to the shelf.
* **Opening hours** on a 24-hour in-game clock, including overnight windows.
* **Shopkeeper peds** streamed by distance, dressed, floor-snapped, with native hold prompts and blips.
* **Localisation** — English, Spanish and Turkish included; add a language by copying one file.

### Framework compatibility

| Framework | Status |
| --------- | --------- |
| VORP Core | Supported |
| RSG Core | Supported |
| Standalone | Supported |

Framework and inventory are **detected automatically**, or can be pinned in `config.lua`. All
framework-specific calls live in a `bridge/` layer, so adapting to another framework means editing
one file.
