---
title: "Switch vehicle lock"
description: "Switch a vehicle's lock, revoking keys previously shared by the owner."
icon: "key"
---

Triggering this event (from client side) will switch the lock of the vehicle with that plate, removing all keys previously shared by the owner to other players.

```lua Event
TriggerServerEvent("vehicles_keys:switchLock", plate)
```

### Parameters

| Name    | Data Type | Description                |
| ------- | --------- | ------------------------------ |
| `plate` | string    | The plate of the vehicle          |
