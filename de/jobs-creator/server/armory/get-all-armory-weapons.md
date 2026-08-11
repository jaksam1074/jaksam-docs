---
title: "Alle Armory-Waffen abrufen"
description: "Rufe die Liste aller Waffen ab, die in einer bestimmten Armory gelagert sind."
icon: "gun"
---

Ruft eine Liste aller Waffen ab, die in einer bestimmten Armory-ID gelagert sind.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getAllArmoryWeapons(markerId)
```

```lua Beispiel
local markerId = 52
local allWeapons = exports["jobs_creator"]:getAllArmoryWeapons(markerId)
print("Waffen aller Spieler in dieser Armory")
print(ESX.DumpTable(allWeapons))
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `markerId` | integer | Die Marker-ID |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `armoryWeapons` | table | Liste aller im Marker gelagerten Waffen |
