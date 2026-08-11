---
title: "Armory-Waffen des Spielers abrufen"
description: "Rufe die Liste der Waffen ab, die ein bestimmter Spieler in einer bestimmten Armory gelagert hat."
icon: "gun"
---

Ruft eine Liste der Waffen eines Spielers ab, die in einer bestimmten Armory-ID gelagert sind.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getPlayerArmoryWeapons(playerId, markerId)
```

```lua Beispiel
local playerId = 20
local markerId = 52
local playerArmoryWeapons = exports["jobs_creator"]:getPlayerArmoryWeapons(playerId, markerId)
print("Waffen des Spielers in dieser Armory")
print(ESX.DumpTable(playerArmoryWeapons))
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `markerId` | integer | Die Marker-ID |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerArmoryWeapons` | table | Liste aller im Marker gelagerten Waffen des Spielers |
