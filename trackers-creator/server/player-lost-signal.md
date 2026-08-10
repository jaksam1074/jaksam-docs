---
title: "Player lost signal"
description: "Triggered server side when a player loses signal of a tracker."
icon: "satellite-dish"
---

This event is triggered when a player loses signal of a tracker, because they lost the required item.

```lua Event
AddEventHandler("trackers_creator:playerLostSignalWithTracker", function(playerId, trackerId)

end)
```

### Parameters

| Name        | Data Type | Description                        |
| ----------- | --------- | ------------------------------------ |
| `playerId`  | integer   | The server ID of the player          |
| `trackerId` | integer   | The tracker ID that lost signal      |

## Example

```lua
RegisterNetEvent("trackers_creator:playerLostSignalWithTracker", function(playerId, trackerId)
    -- You can use any code here to retrieve data from the database or do anything
end)
```
