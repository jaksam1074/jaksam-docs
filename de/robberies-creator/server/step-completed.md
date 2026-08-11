---
title: "Schritt abgeschlossen"
description: "Wird ausgelöst, wenn ein Schritt eines Heists abgeschlossen wird."
icon: "circle-check"
---

Wird ausgelöst, wenn ein Schritt eines Heists abgeschlossen wird.

```lua Event
RegisterNetEvent("robberies_creator:heist:stepCompleted", function(playerId, heistId, stageId, stepType)

end)
```

### Parameter

| Name       | Datentyp | Beschreibung                                                                              |
| ---------- | --------- | -------------------------------------------------------------------------------------------- |
| `playerId` | integer   | Server-ID des Spielers, der den Schritt abgeschlossen hat                                                       |
| `heistId`  | integer   | Heist-ID                                                                                        |
| `stageId`  | integer   | Stufen-ID                                                                                        |
| `stepType` | string    | Der Schritttyp. Verfügbare Schritttypen sind [unten](#schritttypen) aufgelistet                            |

### Schritttypen

- `SAFE`
- `ROBBABLE_OBJECT`
- `HACKABLE_PANEL`
- `THERMAL_CHARGE`
- `LOCKPICKABLE_DOOR`

## Beispiel

```lua
-- Dieses hypothetische Beispiel gibt XP, wenn ein Spieler einen Schritt mit einem Minigame abschließt
RegisterNetEvent("robberies_creator:heist:stepCompleted", function(playerId, heistId, stageId, stepType)
    if(stepType ~= "ROBBABLE_OBJECT") then
        TriggerEvent("xp_script:addPlayerXp", playerId, 10)
    end
end)
```

<Note>
  Platziere diesen Code in der Datei `integrations/sv_integrations.lua` des Scripts, am Ende der Datei in neuen Zeilen.
</Note>
