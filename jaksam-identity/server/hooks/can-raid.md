---
title: "Can raid"
description: "Add your own conditions to break the door of a forgery workshop open."
icon: "building-shield"
---

Called when an officer starts breaking the door of a workshop open. The force and rank, being on duty, enough officers online, the door ram item and the wait since the last raid are checked before. Return `false` to block the breach.

Edit `Editable.CanRaid` in `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.CanRaid(src, workshopId)
    return true
end
```

```lua Example
-- Raids need a warrant from your MDT
function Editable.CanRaid(src, workshopId)
    return exports["my_mdt"]:HasWarrant("workshop", workshopId)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `src` | integer | Server ID of the officer |
| `workshopId` | string | The workshop ID, a key of `Config.Forgery.workshops` |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `allowed` | boolean | **true** to allow the breach |
