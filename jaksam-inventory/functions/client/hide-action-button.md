---
title: "Hide action button"
description: "Hides an action button from the inventory UI without removing it."
icon: "eye-slash"
---

Hides an action button from the inventory UI without removing it.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:hideActionButton(id)
```

```lua Example
-- Hide a button temporarily
exports['jaksam_inventory']:hideActionButton('police_actions')

-- Hide button when player is off-duty
AddEventHandler('esx:setJob', function(job)
    if job.name ~= 'police' then
        exports['jaksam_inventory']:hideActionButton('police_actions')
    end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `id` | string | The unique identifier of the button to hide |

### Return value

None.
