---
title: "Fahrzeug-Kennzeichen selbst geben"
description: "Gib dir selbst die Schlüssel eines bestimmten Fahrzeug-Kennzeichens."
icon: "key"
---

Du kannst dieses Event nutzen, um dir selbst ein Fahrzeug-Kennzeichen zu geben, zum Beispiel bei Events, bei denen dein Framework ein Fahrzeug mit dem `/car`-Befehl spawnt.

```lua Event
TriggerServerEvent("vehicles_keys:selfGiveVehicleKeys", plate)
```

### Hinweis

Wenn du einen einfacheren Weg möchtest, dir selbst die Schlüssel des Fahrzeugs zu geben, das du gerade fährst, sieh dir [diese Seite](/de/vehicles-keys/client/self-give-current-vehicle-plate) an.
