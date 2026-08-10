---
title: "Get queue info"
description: "Get the data of the players who are currently in queue."
icon: "circle-info"
---

Use the following export to get the data of the players who are currently in queue (nickname, identifier, priority, etc.).

```lua Export
-- Returns a table
exports["easy_allowlist"]:getPlayersInQueue()
```

## Example

```lua
RegisterCommand("queueinfo", function(source, args)
    local queueInfo = exports["easy_allowlist"]:getPlayersInQueue()
    print(json.encode(queueInfo, { indent = true }))
end, false)
```

<Note>
  You can add this code in `sv_integrations.lua` of the script or in any other server-side Lua file.
</Note>
