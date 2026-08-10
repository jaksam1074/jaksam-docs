---
title: "Unregister action button"
description: "Removes a previously registered action button from the inventory UI."
icon: "square-minus"
---

Removes a previously registered action button from the inventory UI.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterActionButton(id)
```

```lua Example
-- Unregister a button when no longer needed
exports['jaksam_inventory']:unregisterActionButton('my_custom_button')

-- Unregister when player leaves a job
AddEventHandler('esx:setJob', function(job)
    if job.name ~= 'police' then
        exports['jaksam_inventory']:unregisterActionButton('police_actions')
    end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `id` | string | The unique identifier of the button to remove (same id used in `registerActionButton`) |

### Return value

None.
