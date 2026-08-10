---
title: "Disable default selling method for NPCs"
description: "Disable the default 'Press E to sell drugs' prompt above NPCs."
icon: "ban"
---

Trigger to disable the prompt above NPCs, `Press E to sell drugs`.

<Note>
  If you disable the prompt, you have to manually trigger the `drugs_creator:sellToNPC` event to sell to NPCs.
</Note>

```lua Event
TriggerEvent("drugs_creator:disableDefaultSellingMethodNPC")
```

## Example

```lua
-- Disables the prompt
RegisterNetEvent("drugs_creator:framework:ready", function()
    TriggerEvent("drugs_creator:disableDefaultSellingMethodNPC")
end)

-- Manually sell to an NPC (example for targeting scripts)
Citizen.CreateThread(function()
    local closestPed = ESX.Game.GetClosestPed()

    TriggerEvent("drugs_creator:sellToNPC", closestPed)
end)
```
