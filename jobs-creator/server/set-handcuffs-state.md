---
title: "Set handcuffs state"
description: "Set a player's handcuffed state directly, without triggering the handcuff animation."
icon: "handcuffs"
---

Set the handcuffs state of a player, without the animation.

<CodeGroup>

```lua Export
exports["jobs_creator"]:setHandcuffs(playerId, state)
```

```lua Example
-- This is just an example and won't work, requires you to use the export properly
RegisterNetEvent("hospital_script:playerDead", function(playerId)
    -- The script code
    -- The script code
    -- The script code

    -- The dead player is not handcuffed anymore
    exports["jobs_creator"]:setHandcuffs(playerId, false)
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | The target player's server ID |
| `state` | boolean | `true` = handcuffed, `false` = free |