---
title: "Weapon Stolen"
description: "Triggered after a player steals something from the actions menu, only if you use the default player search/rob, it won't work if you replaced it"
icon: "gun"
---

Triggered after a player steals a weapon from the actions menu.

<Note>
  This only works if you use the default player search/rob action — it won't fire if you replaced it with a custom module.
</Note>

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:weaponStolen", function(playerId, targetId, weaponName)
end)
```

```lua Example
-- This example for ESX will "delete" the stolen weapons (maybe useful for cops)
RegisterNetEvent("jobs_creator:actions:weaponStolen", function(playerId, targetId, weaponName)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    xPlayer.removeWeapon(weaponName)
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | The server ID of the player who stole the weapon |
| `targetId` | integer | The server ID of the victim who lost the weapon |
| `weaponName` | string | Weapon name |