---
title: "Admin shop sold object"
description: "Triggered when a player sells an object to an admin shop."
icon: "hand-holding-dollar"
---

Triggered after a player sells an object to an admin shop.

```lua Event
RegisterNetEvent("shops_creator:adminShops:soldObject", function(playerId, shopId, itemId, quantity, totalPrice)

end)
```

### Parameters

| Name         | Data Type | Description                                     |
| ------------ | --------- | -------------------------------------------------- |
| `playerId`   | integer   | The player ID who sold the object                    |
| `shopId`     | integer   | The shop ID (the same one that's in the database)   |
| `itemId`     | string    | The item ID that was sold                             |
| `quantity`   | integer   | The quantity of items sold                             |
| `totalPrice` | integer   | The total price of the items sold                      |

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
