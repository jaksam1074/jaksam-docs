---
title: "Territoriums-Besitzer abrufen"
description: "Ruft den aktuellen Besitzer jedes Territoriums ab."
icon: "flag"
---

Gibt eine Table mit dem aktuellen Besitzer jedes Territoriums zurück.

```lua Export
local owners = exports["drugs_creator"]:getTerritoryOwners()
```

### Rückgabe

| Datentyp | Beschreibung                                                                    |
| --------- | ----------------------------------------------------------------------------------- |
| table     | Eine Table, bei der Key = Territoriumsname und Value = besitzender Job-/Gang-Name oder `nil`         |

## Beispiel

```lua
local owners = exports["drugs_creator"]:getTerritoryOwners()

for territoryName, ownerFaction in pairs(owners) do
    print(territoryName .. " is owned by " .. (ownerFaction or "nobody"))
end
```
