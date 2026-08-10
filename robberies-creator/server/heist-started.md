---
title: "Heist started"
description: "Triggered when a heist starts."
icon: "play"
---

Triggered when a step is finished in the first stage of a heist that hasn't started yet.

```lua Event
RegisterNetEvent("robberies_creator:heist:heistStarted", function(heistId)

end)
```

### Parameters

| Name      | Data Type | Description        |
| --------- | --------- | --------------------- |
| `heistId` | integer   | ID of the heist        |

## Example

```lua
RegisterNetEvent("robberies_creator:heist:heistStarted", function(heistId)
    -- just an example, will do nothing useful, you may want to retrieve data from the database

    print("Heist with ID " .. heistId .. " has just started")
end)
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
