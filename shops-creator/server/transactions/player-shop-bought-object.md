---
title: "Player shop bought object"
description: "Triggered when a player buys an object from a player-owned shop."
icon: "hand-holding-dollar"
---

Triggered after a player buys an object from a player-owned shop.

```lua Event
RegisterNetEvent("shops_creator:playersShops:boughtObject", function(playerId, shopId, objectId, quantity, totalPrice)

end)
```

### Parameters

| Name         | Data Type | Description                                     |
| ------------ | --------- | -------------------------------------------------- |
| `playerId`   | integer   | The player ID who bought the object                 |
| `shopId`     | integer   | The shop ID (the same one that's in the database)   |
| `objectId`   | integer   | The object ID that was bought                         |
| `quantity`   | integer   | The quantity of items bought                          |
| `totalPrice` | integer   | The total price of the items bought                   |

<Note>
  Place this code in the file `integrations/sv_integrations.lua` of the script, at the bottom of the file on new lines.
</Note>
