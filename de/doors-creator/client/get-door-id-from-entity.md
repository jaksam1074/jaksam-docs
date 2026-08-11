---
title: "Tür-ID aus Entität abrufen"
description: "Ermittelt eine Tür-ID anhand ihres Entitäts-Handles."
icon: "magnifying-glass"
---

```lua Export
exports["doors_creator"]:getDoorIdFromEntity(entity)
```

### Parameter

| Name     | Datentyp | Beschreibung                                  |
| -------- | --------- | ----------------------------------------------- |
| `entity` | integer   | Das Entitäts-Handle, aus dem die Tür-ID ermittelt werden soll        |

### Rückgabe

| Datentyp | Beschreibung                            |
| --------- | ----------------------------------------- |
| integer   | Die Tür-ID, falls gefunden, sonst `nil`      |

## Beispiel

```lua
-- Dieses Beispiel zeigt, wie man eine Target-Option zum Prüfen von Tür-IDs mit ox_target hinzufügt
-- Hinweis: Dies ist nur ein Beispiel, du musst es an deine Bedürfnisse und dein Target-System anpassen
Citizen.CreateThread(function()
    exports.ox_target:addGlobalObject({
        {
            name = 'check_door_id',
            icon = 'fas fa-door-open',
            label = 'Check Door ID',
            onSelect = function(data)
                local doorId = exports["doors_creator"]:getDoorIdFromEntity(data.entity)

                if doorId then
                    print("Found door with ID: " .. doorId)
                end
            end
        }
    })
end)
```
