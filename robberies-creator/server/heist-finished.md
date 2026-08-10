---
title: "Heist finished"
description: "Triggered when a heist is completed."
icon: "flag-checkered"
---

Triggered when a heist is completed (the same moment the server console logs `"Heist has been completed"`).

```lua Event
RegisterNetEvent("robberies_creator:heist:heistFinished", function(heistId)

end)
```

### Parameters

| Name      | Data Type | Description        |
| --------- | --------- | --------------------- |
| `heistId` | integer   | ID of the heist        |

## Example

```lua
RegisterNetEvent("robberies_creator:heist:heistFinished", function(heistId)
    -- just an example, will do nothing useful, you may want to retrieve data from the database

    print("Heist with ID " .. heistId .. " is finished")
end)
```

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
