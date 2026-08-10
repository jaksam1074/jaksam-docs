---
title: "Register action button"
description: "Registers a custom action button in the inventory UI toolbar."
icon: "square-plus"
---

Registers a custom action button in the inventory UI toolbar. Action buttons appear on the right side of the inventory and can trigger any custom logic when clicked.

<Tip>
  For a complete guide with images and examples, see the [Action Buttons Guide](/jaksam-inventory/guides/action-buttons).
</Tip>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerActionButton(id, icon, tooltip, onClick, visible)
```

```lua Example
-- Register a simple action button
exports['jaksam_inventory']:registerActionButton(
    'my_custom_button',
    'bi-star-fill',
    'My Custom Action',
    function()
        print('Button clicked!')
        -- Your custom logic here
    end
)

-- Register a hidden button (to show later based on conditions)
exports['jaksam_inventory']:registerActionButton(
    'police_actions',
    'bi-shield-check',
    'Police Actions',
    function()
        TriggerEvent('myPoliceScript:openMenu')
    end,
    false -- hidden by default
)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `id` | string | Unique identifier for the button. Used to reference the button when showing/hiding/unregistering |
| `icon` | string | Bootstrap Icons class name (e.g. "bi-shield-x", "bi-car-front-fill"). Find icons at [icons.getbootstrap.com](https://icons.getbootstrap.com/) |
| `tooltip` | string \| nil | Tooltip text shown when hovering the button. Can be nil for no tooltip |
| `onClick` | function | Callback function executed when the button is clicked |
| `visible` | boolean \| nil | Whether the button should be visible initially. Default: true |

### Return value

None.
