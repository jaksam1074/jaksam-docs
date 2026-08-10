---
title: "UI toggled"
description: "Hide or show your own UI when the shop UI is toggled."
icon: "eye"
---

Useful to hide/show your UI when the shop UI is toggled.

## Shop UI activated

```lua
RegisterNetEvent("shops_creator:ui:show", function()
    -- Disable your UI here with your own code
end)
```

## Shop UI disabled

```lua
RegisterNetEvent("shops_creator:ui:hide", function()
    -- Enable your UI here with your own code
end)
```

<Note>
  Place this code in the file `integrations/cl_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
