---
title: "Ped von Verkaufs-Blacklist entfernen"
description: "Erlaube, dass einem zuvor blockierten Ped wieder Drogen verkauft werden können."
icon: "user-check"
---

Entfernt einen Ped von der NPC-Verkaufs-Blacklist — das Gegenteil des Exports `addPedToNPCSellingBlacklist`.

```lua Export
exports["drugs_creator"]:removePedFromNPCSellingBlacklist(ped)
```

### Parameter

| Name  | Datentyp       | Beschreibung             |
| ----- | ---------------- | -------------------------- |
| `ped` | ped (integer)     | Das Handle des Ziel-Peds       |

## Beispiel

```lua
RegisterNetEvent('drugs_creator:framework:ready', function()
    local closestPed = ESX.Game.GetClosestPed()

    exports["drugs_creator"]:removePedFromNPCSellingBlacklist(closestPed)
end)
```
