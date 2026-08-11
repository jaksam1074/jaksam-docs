---
title: "Mission fehlgeschlagen"
description: "Wird server-seitig ausgelöst, wenn eine Mission fehlschlägt."
icon: "circle-xmark"
---

Event, das beim Fehlschlagen einer Mission ausgelöst wird.

```lua Event
RegisterNetEvent("missions_creator:missionFailed", function(instanceId, missionId, players, reason)

end)
```

### Parameter

| Name         | Datentyp | Beschreibung                                       |
| ------------ | --------- | ---------------------------------------------------- |
| `instanceId` | integer   | Eindeutige Sitzungs-ID                                     |
| `missionId`  | integer   | Missions-ID, die du im Admin-Menü siehst         |
| `players`    | table     | Table mit den Spielern, die an der Mission teilgenommen haben |
| `reason`     | string    | Der Grund, warum die Mission fehlgeschlagen ist                     |

<Note>
  Füge dieses Event in jeder server-seitigen Datei hinzu, in der du es nutzen möchtest.
</Note>
