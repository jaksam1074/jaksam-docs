---
title: "Mission abgeschlossen"
description: "Wird server-seitig ausgelöst, wenn eine Mission erfolgreich abgeschlossen wird."
icon: "circle-check"
---

Event, das bei erfolgreichem Abschluss einer Mission ausgelöst wird.

```lua Event
RegisterNetEvent("missions_creator:missionCompleted", function(instanceId, missionId, players)

end)
```

### Parameter

| Name         | Datentyp | Beschreibung                                       |
| ------------ | --------- | ---------------------------------------------------- |
| `instanceId` | integer   | Eindeutige Sitzungs-ID                                     |
| `missionId`  | integer   | Missions-ID, die du im Admin-Menü siehst         |
| `players`    | table     | Table mit den Spielern, die an der Mission teilgenommen haben |

<Note>
  Füge dieses Event in jeder server-seitigen Datei hinzu, in der du es nutzen möchtest.
</Note>
