---
title: "Menü manuell öffnen"
description: "Löst das Öffnen des Blips-Creator-Menüs aus deinem eigenen client-seitigen Code aus."
icon: "map-location-dot"
---

Du kannst dieses Event von überall **client-seitig** nutzen, um das Menü zu öffnen.

```lua Event
TriggerEvent("blips_creator:openBlipsMenu")
```

## Beispiel

Du kannst das Menü z.B. mit einem Befehl öffnen:

```lua
RegisterCommand("blipscreator", function()
    TriggerEvent("blips_creator:openBlipsMenu")
end)
```
