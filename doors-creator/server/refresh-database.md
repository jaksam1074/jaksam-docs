---
title: "Refresh database"
description: "Refresh Doors Creator after manually creating something in the database."
icon: "rotate"
---

Useful to refresh Doors Creator after you manually create something in the database.

```lua Export
exports["doors_creator"]:refreshDatabase()
```

## Example

```lua
RegisterCommand("refreshDoorsCreator", function(playerId)
    -- Only server console can use the command
    if(playerId and playerId > 0) then return end

    exports["doors_creator"]:refreshDatabase()
end)
```
