---
title: "Fahrzeuge des Spielers in Marker-ID abrufen"
description: "Rufe alle Fahrzeuge ab, die ein Spieler in einem bestimmten kaufbaren Garagen-Marker besitzt."
icon: "car"
---

Ruft alle Fahrzeuge ab, die eine Spieler-ID in einer bestimmten kaufbaren Garagen-Marker-ID besitzt.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getPlayerVehiclesInMarkerId(playerId, markerId)
```

```lua Beispiel
local playerId = 1
local markerId = 252
local playerVehiclesInMarker = exports["jobs_creator"]:getPlayerVehiclesInMarkerId(playerId, markerId)
print(ESX.DumpTable(playerVehiclesInMarker))
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `markerId` | integer | Marker-ID |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicles` | table | Tabelle mit allen Fahrzeugen, die der Spieler in der Garage besitzt, Key ist die Fahrzeug-ID, Wert sind die Fahrzeugdaten |
