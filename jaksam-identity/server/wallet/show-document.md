---
title: "Show document"
description: "Show a document the player carries to a player nearby as the 3D card."
icon: "eye"
---

Shows a carried document to another player as the 3D card, exactly as if it was shown from the inventory. The player must carry the document, and both players must be in the same instance and within `Config.ShowDistance`.

<CodeGroup>

```lua Export
exports["jksm_identity"]:ShowDocument(playerId, targetId, serial)
```

```lua Example
RegisterNetEvent("my_phone:showCard", function(targetId, serial)
    local ok, reason = exports["jksm_identity"]:ShowDocument(source, targetId, serial)
    if not ok then
        TriggerClientEvent("my_phone:notify", source, "Could not show the card: " .. reason)
    end
end)
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Server ID of the player who shows the document |
| `targetId` | integer | Server ID of the player who sees it |
| `serial` | string | The number of a document the player carries |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `ok` | boolean | **true** if the card was shown |
| `reason` | string \| nil | `bad_target` (invalid or same player), `too_far` (other instance or too far away), `no_card` (the player doesn't carry that document) |
