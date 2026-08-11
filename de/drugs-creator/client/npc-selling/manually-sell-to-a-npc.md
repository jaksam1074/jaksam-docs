---
title: "Manuell an NPC verkaufen"
description: "Starte einen Drogenverkauf an einen bestimmten Ped manuell."
icon: "hand-holding"
---

Auslösen, um den Verkauf an einen NPC zu starten, so wie es passiert, wenn man in der Standardmethode E zum Verkaufen drückt.

```lua Event
TriggerEvent("drugs_creator:sellToNPC", ped)
```

### Parameter

| Name  | Datentyp       | Beschreibung             |
| ----- | ---------------- | -------------------------- |
| `ped` | ped (integer)     | Das Handle des Ziel-Peds       |

## Beispiel

```lua
local closestPed = ESX.Game.GetClosestPed()

TriggerEvent("drugs_creator:sellToNPC", closestPed)
```
