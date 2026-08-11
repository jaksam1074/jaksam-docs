---
title: "Drogeneffekte manuell starten"
description: "Löse Drogeneffekte manuell aus, client- oder server-seitig."
icon: "wand-magic-sparkles"
---

Auslösen, um Drogeneffekte zu starten (du löst dies eventuell lieber server-seitig aus).

```lua Event
TriggerEvent("drugs_creator:drugEffects", takingMethod, effects, effectsDuration, cumulativeEffects)
```

### Parameter

| Name                | Datentyp | Beschreibung                                                                                        |
| -------------------- | --------- | -------------------------------------------------------------------------------------------------------- |
| `takingMethod`        | string    | Wie der Spieler die Droge zu sich nimmt                                                                           |
| `effects`             | table     | Ein Array von Strings mit allen Effekten, die hinzugefügt werden sollen                                                  |
| `effectsDuration`     | integer   | Sekunden, die die Effekte anhalten                                                                                |
| `cumulativeEffects`   | table     | Optional. Array mit den kumulativen Effekten, die hinzugefügt werden sollen (siehe Beispiele für das Format)         |

### Einnahmemethoden

- `"pill"`
- `"drink"`
- `"smoke"`
- `"needle"`

### Effekte

- `"visual_shaking"`
- `"drunk_walk"`
- `"fall"`
- `"pink_visual"`
- `"green_visual"`
- `"confused_visual"`
- `"yellow_visual"`
- `"blurred_visual"`
- `"red_visual"`
- `"foggy_visual"`
- `"blue_visual"`
- `"armor50"`
- `"armor100"`
- `"health50"`
- `"health100"`
- `"sprint_faster"`
- `"swim_faster"`
- `"infinite_stamina"`
- `"remove_old_effects"`
- `"vehicle_stalker"`
- `"ghost"`

### Kumulative Effekte `actions`

- `increaseArmor`
- `decreaseArmor`
- `increaseHealth`
- `decreaseHealth`
- `increaseHunger`
- `decreaseHunger`
- `increaseThirst`
- `decreaseThirst`
- `increaseStress`
- `decreaseStress`

## Beispiel — Client-seitig

```lua
RegisterCommand("effects", function()
    local takingMethod = "pill"
    local effects = {
        "drunk_walk",
        "swim_faster",
        "green_visual",
    }

    local cumulativeEffects = {
        {action = "increaseArmor", value = 50},
        {action = "decreaseThirst", value = 15},
    }

    local effectsDuration = 120 -- Sekunden

    TriggerEvent("drugs_creator:drugEffects", takingMethod, effects, effectsDuration, cumulativeEffects)
end)
```

## Beispiel — Server-seitig

```lua
RegisterCommand("effects", function(playerId)
    local takingMethod = "pill"
    local effects = {
        "drunk_walk",
        "swim_faster",
        "green_visual",
    }

    local cumulativeEffects = {
        {action = "increaseArmor", value = 50},
        {action = "decreaseThirst", value = 15},
    }

    local effectsDuration = 120 -- Sekunden

    TriggerClientEvent("drugs_creator:drugEffects", playerId, takingMethod, effects, effectsDuration, cumulativeEffects)
end)
```
