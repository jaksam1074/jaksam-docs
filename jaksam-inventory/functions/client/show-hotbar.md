---
title: "Show hotbar"
description: "Shows the hotbar UI with the first 5 slots of the player's inventory."
icon: "grip"
---

Shows the hotbar UI with the first 5 slots of the player's inventory.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:showHotbar()
```

```lua Example
-- Show hotbar
exports['jaksam_inventory']:showHotbar()

-- Show hotbar after receiving an item
AddEventHandler('myScript:itemReceived', function()
    exports['jaksam_inventory']:showHotbar()
end)
```

</CodeGroup>

### Parameters

None.

### Return value

None. Shows the hotbar UI which automatically hides after 2 seconds.

### Notes

- The hotbar shows slots 1-5 from the player's inventory
- If `config.dynamicHotbar` is true, empty slots at the end are hidden
- The hotbar automatically hides after 2 seconds
- Multiple calls reset the hide timer
