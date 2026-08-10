---
title: "Panic button pressed"
description: "Triggered server side when a player uses the panic button."
icon: "triangle-exclamation"
---

This event is triggered when a player uses the panic button.

```lua Event
AddEventHandler("trackers_creator:playerPressedPanicButton", function(playerId)

end)
```

### Parameters

| Name       | Data Type | Description                                              |
| ---------- | --------- | ---------------------------------------------------------- |
| `playerId` | integer   | The server ID of the player who pressed the panic button   |

## Example

```lua
RegisterNetEvent("trackers_creator:playerPressedPanicButton", function(playerId)
    local name = GetPlayerName(playerId)
    local plyPed = GetPlayerPed(playerId)
    local coords = GetEntityCoords(plyPed)

    print("Player " .. name .. " pressed panic button in coordinates " .. tostring(coords))
end)
```
