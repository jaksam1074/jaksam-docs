---
title: "Pocket crafting finished"
description: "Triggered server side when a player completes a pocket crafting process."
icon: "flask-vial"
---

This event is triggered after a player successfully completes a pocket crafting process. It's fired right after the player receives their crafted item.

```lua Event
AddEventHandler("drugs_creator:pocketCraftingFinished", function(playerId, itemName)

end)
```

### Parameters

| Name        | Data Type | Description                                                  |
| ----------- | --------- | ------------------------------------------------------------- |
| `playerId`  | integer   | The server ID of the player who completed the crafting            |
| `itemName`  | string    | The name of the pocket crafting item that was used                 |

## Example

```lua
AddEventHandler("drugs_creator:pocketCraftingFinished", function(playerId, itemName)
    print("Player " .. playerId .. " finished crafting with " .. itemName)
end)
```
