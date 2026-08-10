---
title: "On mission failed"
description: "Triggered server side when a mission fails."
icon: "circle-xmark"
---

Event triggered on mission fail.

```lua Event
RegisterNetEvent("missions_creator:missionFailed", function(instanceId, missionId, players, reason)

end)
```

### Parameters

| Name         | Data Type | Description                                       |
| ------------ | --------- | ---------------------------------------------------- |
| `instanceId` | integer   | Unique session ID                                     |
| `missionId`  | integer   | Mission ID, the one you see in the admin menu         |
| `players`    | table     | Table containing the players who participated in the mission |
| `reason`     | string    | The reason the mission has failed                     |

<Note>
  Add this event in any server-side file you want to use it in.
</Note>
