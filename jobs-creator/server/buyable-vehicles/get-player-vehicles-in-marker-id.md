---
title: "Get player vehicles in marker ID"
description: "Retrieve all vehicles a player owns in a specific buyable garage marker."
icon: "car"
---

Get all vehicles owned by a player ID in a specific buyable garage marker ID.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getPlayerVehiclesInMarkerId(playerId, markerId)
```

```lua Example
local playerId = 1
local markerId = 252
local playerVehiclesInMarker = exports["jobs_creator"]:getPlayerVehiclesInMarkerId(playerId, markerId)
print(ESX.DumpTable(playerVehiclesInMarker))
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |
| `markerId` | integer | Marker ID |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `vehicles` | table | Table with all vehicles owned by the player in the garage, key is vehicle ID and value is the vehicle data |