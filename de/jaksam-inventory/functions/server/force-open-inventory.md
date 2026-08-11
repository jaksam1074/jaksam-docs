---
title: "Force open inventory"
description: "Erzwingt das Öffnen eines Inventars für einen bestimmten Spieler, ohne Berechtigungsprüfung."
icon: "door-open"
---

Erzwingt das Öffnen eines Inventars für einen bestimmten Spieler, ohne Berechtigungsprüfung.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:forceOpenInventory(playerId, inventoryId)
```

```lua Example
-- Einen Stash für einen Spieler öffnen
local playerId = 1
exports['jaksam_inventory']:forceOpenInventory(playerId, 'police_stash_1')

-- Das Inventar eines anderen Spielers öffnen (durchsuchen/ausrauben)
local targetPlayerId = 2
exports['jaksam_inventory']:forceOpenInventory(playerId, targetPlayerId)

-- Inventar über ein eigenes Menü/UI öffnen
RegisterNetEvent('myresource:openCustomStorage', function(storageId)
    local playerId = source
    exports['jaksam_inventory']:forceOpenInventory(playerId, storageId)
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | number | Die Server-ID des Spielers, der das Inventar sieht |
| `inventoryId` | string \| number | Die zu öffnende Inventar-ID. Kann eine Spieler-Server-ID (number) oder Inventar-ID (string) sein |

### Rückgabewert

Keiner.
