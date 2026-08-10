---
title: "Player set new private frequency"
description: "Triggered server side when a player sets a new private tracker frequency."
icon: "sliders"
---

This event is triggered when a player uses the private tracker item and sets a new frequency.

```lua Event
AddEventHandler("trackers_creator:playerSetNewPrivateFrequency", function(playerId, trackerId)

end)
```

### Parameters

| Name        | Data Type | Description                 |
| ----------- | --------- | ------------------------------ |
| `playerId`  | integer   | The server ID of the player     |
| `frequency` | integer   | New frequency chosen            |
