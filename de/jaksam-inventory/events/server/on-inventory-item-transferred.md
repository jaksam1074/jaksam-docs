---
title: "Inventory item transferred"
description: "Wird ausgelöst, wenn ein Item erfolgreich von einem Inventar zu einem anderen übertragen wurde."
icon: "right-left"
---

Wird ausgelöst, wenn ein Item erfolgreich von einem Inventar zu einem anderen übertragen wurde (inklusive Bewegungen innerhalb desselben Inventars).

<CodeGroup>

```lua Event
AddEventHandler('jaksam_inventory:onInventoryItemTransferred', function(inventoryIdFrom, inventoryIdTo, itemName, amount, metadata, slotIdFrom, slotIdTo)
end)
```

```lua Example
AddEventHandler('jaksam_inventory:onInventoryItemTransferred', function(inventoryIdFrom, inventoryIdTo, itemName, amount, metadata, slotIdFrom, slotIdTo)
    local inventoryTypeFrom = exports['jaksam_inventory']:getInventoryType(inventoryIdFrom)
    local inventoryTypeTo = exports['jaksam_inventory']:getInventoryType(inventoryIdTo)
    if inventoryTypeFrom ~= 'player' or inventoryTypeTo ~= 'player' then return end -- Nur Spieler-Inventare behandeln

    print(string.format("Item %s (x%d) transferred from %s to %s", itemName, amount, inventoryIdFrom, inventoryIdTo))

    -- Für QBCore
    local PlayerFrom = exports['qb-core']:GetPlayerByCitizenId(inventoryIdFrom)
    local PlayerTo = exports['qb-core']:GetPlayerByCitizenId(inventoryIdTo)

    if PlayerFrom and PlayerTo then
        local playerIdFrom = PlayerFrom.PlayerData.source
        local playerIdTo = PlayerTo.PlayerData.source
        print(string.format("Player %d transferred item %s (x%d) to player %d", playerIdFrom, itemName, amount, playerIdTo))
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryIdFrom` | string | Die Quell-Inventar-Kennung. Bei Spielern ist das die Charakter-Identifier |
| `inventoryIdTo` | string | Die Ziel-Inventar-Kennung. Bei Spielern ist das die Charakter-Identifier |
| `itemName` | string | Der Name des übertragenen Items |
| `amount` | number | Die übertragene Menge |
| `metadata` | table | Die Metadaten des Items |
| `slotIdFrom` | number \| nil | Der Slot, aus dem das Item übertragen wurde |
| `slotIdTo` | number \| nil | Der Slot, zu dem das Item übertragen wurde |

<Warning>
  Die Quelldokumentation wies auf einen echten Lua-Bug im Originalbeispiel hin (unausgeglichene `end`-Blöcke und eine undefinierte Variable), der in einem früheren Durchgang zum oben gezeigten, funktionierenden Code korrigiert wurde, nach dem gleichen QBCore-Muster wie die anderen Events. Es lohnt sich zu prüfen, ob das zu deiner tatsächlichen Logik passt.
</Warning>
