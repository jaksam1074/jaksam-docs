---
title: "Ped zur Verkaufs-Blacklist hinzufügen"
description: "Verhindere, dass einem bestimmten Ped Drogen verkauft werden können, zum Beispiel Ladenbesitzern oder Dealern."
icon: "user-slash"
---

Fügt einen Ped zur NPC-Verkaufs-Blacklist hinzu, sodass Spieler nicht an diesen Ped verkaufen können (Beispiel: Blackjack-Dealer, Ladenbesitzer, usw.).

<Note>
  Falls du einen einfacheren Weg bevorzugst, kannst du ganze Ped-Modelle in `drugs_creator/integrations/cl_integrations.lua` blockieren.
</Note>

```lua Export
exports["drugs_creator"]:addPedToNPCSellingBlacklist(ped)
```

### Parameter

| Name  | Datentyp       | Beschreibung             |
| ----- | ---------------- | -------------------------- |
| `ped` | ped (integer)     | Das Handle des Ziel-Peds       |

## Beispiel

```lua
RegisterNetEvent('drugs_creator:framework:ready', function()
    local closestPed = ESX.Game.GetClosestPed()

    exports["drugs_creator"]:addPedToNPCSellingBlacklist(closestPed)
end)
```
