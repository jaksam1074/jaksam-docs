---
title: "Shop sold"
description: "Triggered when a player sells a player-owned shop."
icon: "hand-holding-dollar"
---

Triggered after a player sells a player-owned shop.

```lua Event
RegisterNetEvent("shops_creator:playersShops:shopSold", function(shopId, ownerIdentifier)

end)
```

### Parameters

| Name         | Data Type | Description                                     |
| ------------ | --------- | -------------------------------------------------- |
| `shopId`     | integer   | The shop ID (the same one that's in the database)   |
| `identifier` | string    | The identifier of the old owner                     |

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
