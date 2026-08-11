---
title: "Get total item amount"
description: "Ermittelt die Gesamtmenge eines bestimmten Items im Inventar des Spielers."
icon: "hashtag"
---

Ermittelt die Gesamtmenge eines bestimmten Items im Inventar des Spielers.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getTotalItemAmount(itemName, metadata)
```

```lua Example
-- Gesamtmenge Brot ermitteln
local breadCount = exports['jaksam_inventory']:getTotalItemAmount('bread')

-- Menge einer bestimmten Waffe anhand der Seriennummer ermitteln
local weaponCount = exports['jaksam_inventory']:getTotalItemAmount('weapon_pistol', {
    serial = "ABC123"
})
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Der Name des zu zählenden Items |
| `metadata` | table | Metadaten, gegen die beim Zählen abgeglichen werden (falls angegeben, werden nur Items mit gleicher Metadata UND gleichem Namen gezählt) |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `totalAmount` | number | Gesamtmenge des Items im Inventar des Spielers |
