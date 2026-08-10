---
title: "Account stolen"
description: "Triggered after a player steals money via the actions menu, only when using the default search/rob action."
icon: "money-bill-transfer"
---

Triggered after a player steals money from the actions menu.

<Note>
  This only works if you use the default player search/rob action — it won't fire if you replaced it with a custom module.
</Note>

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:accountStolen", function(playerId, targetId, accountName, amount)
end)
```

```lua Example
RegisterNetEvent("jobs_creator:actions:accountStolen", function(playerId, targetId, accountName, amount)
    print(GetPlayerName(playerId) .. " has stolen " .. amount .. " " .. accountName .. " from " .. GetPlayerName(targetId))
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | The server ID of the player who stole the money |
| `targetId` | integer | The server ID of the victim who lost the money |
| `accountName` | string | Account name (example: "bank") |
| `amount` | integer | Amount stolen |