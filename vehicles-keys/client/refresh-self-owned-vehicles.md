---
title: "Refresh self owned vehicles"
description: "Refresh the local player's owned vehicles list client side, for example after buying a new vehicle."
icon: "rotate"
---

Triggering this event (from client side) will refresh the list of the player's owned vehicles (from `owned_vehicles` on ESX or `player_vehicles` on QBCore).

This is useful to update the list of owned vehicles when a player buys a new vehicle — you can add this line of code right after a successful vehicle purchase.

```lua Event
TriggerServerEvent("vehicles_keys:refreshMineOwnedVehicles")
```
