---
title: "Open billing menu"
description: "Open the billing UI menu directly for a known target, without requiring the player to click one."
icon: "file-invoice-dollar"
---

Trigger to open the billing UI menu without requiring the player to select the target player with the mouse.

```lua Event
TriggerEvent("billing_ui:openBillingMenu", targetServerID)
```

### Parameters

| Name             | Data Type | Description                  |
| ----------------- | --------- | -------------------------------- |
| `targetServerID`  | integer   | Target server ID, or `nil`         |

## Example

```lua
local closestPlayer = ESX.Game.GetClosestPlayer()
local targetPlayerId = GetPlayerServerId(closestPlayer)

TriggerEvent("billing_ui:openBillingMenu", targetPlayerId)
```
