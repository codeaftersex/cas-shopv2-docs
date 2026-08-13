# Requirements

CAS Shops & Stores is intentionally light. There is **no database, no SQL import and no build step**.

| Requirement | Notes |
| --- | --- |
| **RedM (RDR3) FXServer** | A current RedM server. |
| **A framework** | One of **VORP Core**, **RSG Core**, or **standalone**. Detected automatically. |
| **An inventory** *(recommended)* | `vorp_inventory` or `rsg-inventory`. Only used to pull item artwork and to check carrying capacity. |

{% hint style="success" %}
**No database.** Stock lives in memory and resets to its configured values whenever the resource
or server restarts. There is nothing to import.
{% endhint %}

{% hint style="warning" %}
Every item name you sell in a shop must exist in your inventory's item database. Weapons
(`weapon_*`) are the exception — they are handled through the framework's weapon storage. The
resource prints an audit of any unknown item names on start (see
[Troubleshooting](troubleshooting.md)).
{% endhint %}
