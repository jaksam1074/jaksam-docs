---
title: "Get if local player is handcuffed"
description: "Check whether the local player is currently handcuffed."
icon: "handcuffs"
---

Returns whether the **local** client/player is handcuffed.

<CodeGroup>

```lua Export
exports["jobs_creator"]:isPlayerHandcuffed()
```

```lua Example
-- This code will continuously check if the local (self) player is handcuffed
-- If so, specified controls will be disabled
Citizen.CreateThread(function()
    while true do
        Citizen.Wait(0)

        if(exports["jobs_creator"]:isPlayerHandcuffed())then
            DisableControlAction(0, 22, true) -- Disable jump
        end
    end
end)
```

</CodeGroup>

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `isHandcuffed` | boolean | `true` if the player is handcuffed, `false` if the player is **not** handcuffed |

### Where to insert the code?

You can place the code in any client file of your scripts.