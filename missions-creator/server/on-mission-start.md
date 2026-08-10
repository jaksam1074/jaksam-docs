---
title: "On mission start"
description: "Triggered server side when a mission starts."
icon: "flag"
---

Event triggered on mission start.

```lua Event
RegisterNetEvent("missions_creator:missionStarted", function(instanceId, missionId, players)

end)
```

### Parameters

| Name         | Data Type | Description                                       |
| ------------ | --------- | ---------------------------------------------------- |
| `instanceId` | integer   | Unique session ID                                     |
| `missionId`  | integer   | Mission ID, the one you see in the admin menu         |
| `players`    | table     | Table containing the players who participated in the mission |

<Note>
  Add this event in any server-side file you want to use it in.
</Note>
