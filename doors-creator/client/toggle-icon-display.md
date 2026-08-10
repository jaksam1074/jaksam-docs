---
title: "Toggle icon display"
description: "Show or hide the icons/text of all doors."
icon: "eye"
---

Toggles icons/text of all doors.

```lua Export
exports["doors_creator"]:toggleIconDisplay(newState)
```

### Parameters

| Name       | Data Type | Description                                          |
| ---------- | --------- | ----------------------------------------------------- |
| `newState` | boolean   | `true` = display icon/text, `false` = hide icon/text   |

## Example

```lua
RegisterCommand("hideDoorsIcon", function()
    exports["doors_creator"]:toggleIconDisplay(false)
end)
```
