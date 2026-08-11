---
title: "Entität gespawnt"
description: "Wird client-seitig ausgelöst, wenn eine Mission einen Ped, ein Fahrzeug oder ein Objekt spawnt."
icon: "cube"
---

```lua Event
RegisterNetEvent("missions_creator:entitySpawned", function(entityType, entity)

end)
```

### Parameter

| Name         | Datentyp | Beschreibung                    |
| ------------ | --------- | -------------------------------- |
| `entityType` | string    | `ped` / `vehicle` / `object`     |
| `entity`     | integer   | Das Handle der Entität               |

## Beispiel

```lua
-- Nur ein Beispiel, das du anpassen kannst, um gespawnten Fahrzeugen Schlüssel zu geben
RegisterNetEvent("missions_creator:entitySpawned", function(entityType, entity)
    if(entityType == "vehicle") then
        local plate = GetVehicleNumberPlateText(entity)
        TriggerEvent("GIVEKEYS", plate)
    end
end)
```

<Note>
  Platziere diesen Code in der Datei `jaksam_core/config/cl_config.lua`, am Ende der Datei in neuen Zeilen.
</Note>
