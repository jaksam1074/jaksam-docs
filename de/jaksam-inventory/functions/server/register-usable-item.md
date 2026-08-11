---
title: "Register usable item"
description: "Registriert eine Callback-Funktion, die aufgerufen wird, wenn ein Item benutzt wird."
icon: "hand-pointer"
---

Registriert eine Callback-Funktion, die aufgerufen wird, wenn ein Item benutzt wird. Framework-spezifisches Registrieren von Items funktioniert trotzdem, wie `ESX.RegisterUsableItem` und das QBCore-Äquivalent.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerUsableItem(itemName, callback)
```

```lua Example: ESX
-- Benutzbares Item auf ESX registrieren
exports['jaksam_inventory']:registerUsableItem('bread', function(playerId, itemName, inventoryItem)
    -- Spieler heilen, wenn Brot benutzt wird
    local plyPed = GetPlayerPed(playerId)
    local health = GetEntityHealth(plyPed)
    SetEntityHealth(plyPed, math.min(health + 20, 200))
end)

-- Benutzbares Item auf ESX registrieren, mit Anzeige der Metadaten
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, itemName, inventoryItem)
    print("Armor has still " .. inventoryItem.metadata.value .. "% of durability")
end)
```

```lua Example: QBCore
-- Benutzbares Item auf QBCore registrieren
exports['jaksam_inventory']:registerUsableItem('armour', function(playerId, item)
    print("Armor has still " .. item.metadata.value .. "% of durability")
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Der Name des zu registrierenden Items |
| `callback` | function | Funktion, die aufgerufen wird, wenn das Item benutzt wird. Parameter bei ESX: `playerId, itemName, inventoryItem` (`name`, `metadata`, `amount`). Parameter bei QBCore: `playerId, inventoryItem` (`name`, `metadata`, `amount`, usw.) |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls die Registrierung erfolgreich war |
