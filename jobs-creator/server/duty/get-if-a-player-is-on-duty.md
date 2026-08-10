---
title: "get-if-a-player-is-on-duty"
---

Returns whether the player is on duty or not.

<CodeGroup>

```lua Export
exports["jobs_creator"]:isPlayerOnDuty(playerId)
```

```lua Example
local playerId = 52
print("Player ID " .. playerId .. " is on duty: " .. tostring(exports["jobs_creator"]:isPlayerOnDuty(playerId)))
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Target player's server ID |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isOnDuty` | boolean | **true** if the player is on-duty, **false** if the player is off-duty |