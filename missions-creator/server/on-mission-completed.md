---
title: "On mission completed"
description: "Triggered server side when a mission succeeds."
icon: "circle-check"
---

Event triggered on mission success.

```lua Event
RegisterNetEvent("missions_creator:missionCompleted", function(instanceId, missionId, players)

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
