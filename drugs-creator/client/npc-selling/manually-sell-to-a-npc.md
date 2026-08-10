---
title: "Manually sell to a NPC"
description: "Manually start a drug sale to a specific ped."
icon: "hand-holding"
---

Trigger to start selling to an NPC, as you would after pressing E to sell in the default method.

```lua Event
TriggerEvent("drugs_creator:sellToNPC", ped)
```

### Parameters

| Name  | Data Type       | Description             |
| ----- | ---------------- | -------------------------- |
| `ped` | ped (integer)     | The target ped's handle       |

## Example

```lua
local closestPed = ESX.Game.GetClosestPed()

TriggerEvent("drugs_creator:sellToNPC", closestPed)
```
