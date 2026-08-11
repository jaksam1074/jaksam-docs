---
title: "Alle Fahrzeuge des Spielers abrufen"
description: "Rufe alle Fahrzeuge ab, die ein Spieler über alle kaufbaren Garagen hinweg besitzt."
icon: "car"
---

Ruft alle Fahrzeuge ab, die eine Spieler-ID in allen kaufbaren Garagen besitzt.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getAllVehiclesOfPlayer(playerId)
```

```lua Beispiel
local playerId = 4
local vehicles = exports["jobs_creator"]:getAllVehiclesOfPlayer(playerId)
print("Fahrzeuge des Spielers:")
print(ESX.DumpTable(vehicles))
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicles` | table | Tabelle mit allen Fahrzeugen, die der Spieler in den kaufbaren Garagen besitzt, Key ist die Fahrzeug-ID, Wert sind die Fahrzeugdaten |
