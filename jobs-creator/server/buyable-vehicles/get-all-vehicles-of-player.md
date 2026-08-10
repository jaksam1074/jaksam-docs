---
title: "Get all vehicles of player"
description: "Retrieve all vehicles a player owns across all buyable garages."
icon: "car"
---

Get all vehicles owned by a player ID in all buyable garages.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getAllVehiclesOfPlayer(playerId)
```

```lua Example
local playerId = 4
local vehicles = exports["jobs_creator"]:getAllVehiclesOfPlayer(playerId)
print("Player vehicles:")
print(ESX.DumpTable(vehicles))
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicles` | table | Table with all vehicles owned by the player in the buyable garages, key is vehicle ID and value is the vehicle data |