---
title: "Mission gestartet"
description: "Wird server-seitig ausgelöst, wenn eine Mission startet."
icon: "flag"
---

Event, das beim Missionsstart ausgelöst wird.

```lua Event
RegisterNetEvent("missions_creator:missionStarted", function(instanceId, missionId, players)

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
