---
title: "Police alerted"
description: "Triggered server side, once per alert, when police is alerted."
icon: "siren-on"
---

<Warning>
  Triggered when police is alerted server side (only **1** time per alert, instead of on each player like the client-side one).
</Warning>

```lua Event
RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)

end)
```

### Parameters

| Name      | Data Type | Description                                |
| --------- | --------- | -------------------------------------------- |
| `coords`  | vector3   | Coordinates where the alert was triggered     |
| `message` | string    | Message that would be displayed               |

## Example

```lua
RegisterNetEvent("missions_creator:alertedPolice", function(coords, message)
    -- just an example, will NOT work
    TriggerClientEvent("news_script:heistAlert", -1, coords, message)
end)
```

<Note>
  Place this code in the file `jaksam_core/config/sv_config.lua`, at the bottom of the file on new lines.
</Note>
