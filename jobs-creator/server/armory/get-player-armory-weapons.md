---
title: "Get player armory weapons"
description: "Retrieve the list of weapons a specific player has stored in a specific armory."
icon: "gun"
---

Get a list of weapons of a player stored in a specific armory ID.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getPlayerArmoryWeapons(playerId, markerId)
```

```lua Example
local playerId = 20
local markerId = 52
local playerArmoryWeapons = exports["jobs_creator"]:getPlayerArmoryWeapons(playerId, markerId)
print("Player weapons in that armory")
print(ESX.DumpTable(playerArmoryWeapons))
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Player server ID |
| `markerId` | integer | The marker ID |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `playerArmoryWeapons` | table | List of all weapons contained in the marker deposited by the player |