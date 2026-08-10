---
title: "Show action button"
description: "Makes a previously hidden action button visible in the inventory UI."
icon: "eye"
---

Makes a previously hidden action button visible in the inventory UI.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:showActionButton(id)
```

```lua Example
-- Show a button that was registered as hidden
exports['jaksam_inventory']:showActionButton('police_actions')

-- Show button when player gets a specific job
AddEventHandler('esx:setJob', function(job)
    if job.name == 'police' then
        exports['jaksam_inventory']:showActionButton('police_actions')
    end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `id` | string | The unique identifier of the button to show |

### Return value

None.
