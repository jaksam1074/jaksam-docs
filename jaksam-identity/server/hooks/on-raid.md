---
title: "On raid"
description: "Send a dispatch call or your own alarm when a raid on a forgery workshop moves on."
icon: "tower-broadcast"
---

Called every time a raid moves on. This is the place for your dispatch call or your own alarm.

Edit `Editable.OnRaid` in `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.OnRaid(workshopId, phase, src)

end
```

```lua Example
function Editable.OnRaid(workshopId, phase, src)
    if phase == "breach" then
        local workshop = Config.Forgery.workshops[workshopId]
        exports["my_dispatch"]:Alert({
            job = "police",
            title = "Raid in progress",
            message = ("Officers are breaching %s"):format(workshop and workshop.label or workshopId),
            coords = src and GetEntityCoords(GetPlayerPed(src)),
        })
    end
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `workshopId` | string | The workshop ID, a key of `Config.Forgery.workshops` (workshops added in game are there too) |
| `phase` | string | `breach` (an officer began to break the door open), `aborted` (the breach was given up), `open` (the door gave way, the officers can go in), `over` (the raid ended, the workshop is sealed) |
| `src` | integer \| nil | Server ID of the officer who did it, **nil** when time ran out or an admin did it |
