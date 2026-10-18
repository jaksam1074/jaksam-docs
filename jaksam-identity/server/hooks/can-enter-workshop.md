---
title: "Can enter workshop"
description: "Add your own conditions to enter a forgery workshop."
icon: "door-open"
---

Called when a player enters a forgery workshop. That the player is a member of the owning job, from the workshop's `minGrade`, is checked before. Return `false` to keep them out.

Edit `Editable.CanEnterWorkshop` in `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.CanEnterWorkshop(src, workshopId)
    return true
end
```

```lua Example
-- Nobody enters while wanted by the police
function Editable.CanEnterWorkshop(src, workshopId)
    return not exports["my_wanted"]:IsWanted(src)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `src` | integer | Server ID of the player |
| `workshopId` | string | The workshop ID, a key of `Config.Forgery.workshops` |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `allowed` | boolean | **true** to let the player in |
