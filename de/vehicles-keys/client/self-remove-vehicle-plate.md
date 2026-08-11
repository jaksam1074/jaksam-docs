---
title: "Fahrzeug-Kennzeichen selbst entfernen"
description: "Entferne deine eigenen Schlüssel für ein bestimmtes Fahrzeug-Kennzeichen."
icon: "key"
---

Du kannst dieses Event nutzen, um ein Fahrzeug-Kennzeichen selbst zu entfernen, zum Beispiel bei Events, bei denen dein Framework ein Fahrzeug mit dem `/dv`-Befehl löscht.

```lua Event
TriggerServerEvent("vehicles_keys:selfRemoveKeys", plate)
```
