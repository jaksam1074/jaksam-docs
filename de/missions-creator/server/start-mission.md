---
title: "Mission starten"
description: "Starte eine Mission server-seitig manuell, zum Beispiel um sie in deinen eigenen Code zu integrieren."
icon: "play"
---

Export, um eine Mission server-seitig manuell zu starten, falls du sie in deinen Code integrieren möchtest.

```lua Export: startMission
exports["missions_creator"]:startMission(templateId, playerIdOrArray)
```

#### Parameter

| Name               | Datentyp       | Beschreibung                                        |
| ------------------ | --------------- | ----------------------------------------------------- |
| `templateId`        | integer         | Die ID der Missionsvorlage                                |
| `playerIdOrArray`   | integer \| table | Server-ID des Spielers, oder ein Array von Spieler-Server-IDs      |

#### Rückgabewert

| Name         | Datentyp | Beschreibung                                                              |
| ------------ | --------- | --------------------------------------------------------------------------- |
| `instanceId` | number    | Die Instanz-ID der neu erstellten Mission, oder `nil`, falls sie nicht erstellt werden konnte |
