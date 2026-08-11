---
title: "Standard-Verkaufsmethode für NPCs deaktivieren"
description: "Deaktiviere die Standard-'Press E to sell drugs'-Aufforderung über NPCs."
icon: "ban"
---

Auslösen, um die Aufforderung `Press E to sell drugs` über NPCs zu deaktivieren.

<Note>
  Wenn du die Aufforderung deaktivierst, musst du das Event `drugs_creator:sellToNPC` manuell auslösen, um an NPCs zu verkaufen.
</Note>

```lua Event
TriggerEvent("drugs_creator:disableDefaultSellingMethodNPC")
```

## Beispiel

```lua
-- Deaktiviert die Aufforderung
RegisterNetEvent("drugs_creator:framework:ready", function()
    TriggerEvent("drugs_creator:disableDefaultSellingMethodNPC")
end)

-- Manuell an einen NPC verkaufen (Beispiel für Targeting-Scripts)
Citizen.CreateThread(function()
    local closestPed = ESX.Game.GetClosestPed()

    TriggerEvent("drugs_creator:sellToNPC", closestPed)
end)
```
