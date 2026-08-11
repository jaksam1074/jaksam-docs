---
title: "Nächstes Fahrzeug-Schloss umschalten"
description: "Schalte das Schloss des nächstgelegenen Fahrzeugs manuell um."
icon: "lock"
---

Dieser Export kann genutzt werden, um das Schloss eines Fahrzeugs manuell umzuschalten.

```lua Export
exports["vehicles_keys"]:toggleClosestVehicleLock()
```

## Beispiel

```lua
RegisterCommand("togglelock", function(_, args)
    exports["vehicles_keys"]:toggleClosestVehicleLock()
end)
```
