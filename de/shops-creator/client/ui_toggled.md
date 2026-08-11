---
title: "UI umgeschaltet"
description: "Verstecke oder zeige dein eigenes UI, wenn das Shop-UI umgeschaltet wird."
icon: "eye"
---

Nützlich, um dein UI zu verstecken/zeigen, wenn das Shop-UI umgeschaltet wird.

## Shop-UI aktiviert

```lua
RegisterNetEvent("shops_creator:ui:show", function()
    -- Deaktiviere hier dein UI mit deinem eigenen Code
end)
```

## Shop-UI deaktiviert

```lua
RegisterNetEvent("shops_creator:ui:hide", function()
    -- Aktiviere hier dein UI mit deinem eigenen Code
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/cl_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
