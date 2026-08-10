---
title: "get-if-player-is-owner-of-vehicle-plate"
---

Returns whether a player ID is the owner of a specific plate.

<CodeGroup>

```lua Export
exports["jobs_creator"]:isPlayerOwnerOfVehiclePlate(playerId, plate)
```

```lua Example
local playerId = 1
local plate = "40PQB261"
local isTheVehicleOwner = exports["jobs_creator"]:isPlayerOwnerOfVehiclePlate(playerId, plate)
print("Is the player owner of that plate: " .. tostring(isTheVehicleOwner))
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player's server ID |
| `plate` | string | Vehicle's plate |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isOwner` | boolean | Whether the player is the vehicle owner or not |