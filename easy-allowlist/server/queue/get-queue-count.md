---
title: "Get queue count"
description: "Get the count of players currently in queue."
icon: "hashtag"
---

Use the following export if you need to get **the count of players currently in queue**.

```lua Export
-- Returns a number
exports["easy_allowlist"]:getQueueCount()
```

## Example

```lua
RegisterCommand("queuecount", function(source, args)
    local queueCount = exports["easy_allowlist"]:getQueueCount()
    print("Queue count: " .. queueCount)
end, false)
```

<Note>
  You can add this code in `sv_integrations.lua` of the script or in any other server-side Lua file.
</Note>
