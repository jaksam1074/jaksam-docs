---
title: "Fortschrittsbalken"
description: "Den Fortschrittsbalken beim Aufbrechen einer Tür, Beschlagnahmen von Beweisen und Schreddern ersetzen."
icon: "spinner"
---

Alles, was Zeit braucht und abgebrochen werden kann (eine Tür aufbrechen, beschlagnahmen, schreddern), läuft über eine Funktion. Standardmäßig ist es `lib.progressBar` aus ox_lib.

Bearbeite `Editable.Progress` in `editable/client.lua`:

<CodeGroup>

```lua Function
function Editable.Progress(seconds, label)
    return lib.progressBar({
        duration = seconds * 1000, label = label, useWhileDead = false, canCancel = true,
        disable = { move = true, car = true, combat = true },
        anim = { dict = 'mini@repair', clip = 'fixing_a_player' },
    }) == true
end
```

```lua Example
function Editable.Progress(seconds, label)
    return exports['my_progressbar']:Start({
        time = seconds * 1000,
        text = label,
        cancelable = true,
    })
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `seconds` | number | Wie lange die Aktion dauert |
| `label` | string | Der Text, der mit dem Fortschrittsbalken angezeigt wird |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `completed` | boolean | **true**, wenn er bis zum Ende lief, **false**, wenn der Spieler abgebrochen hat |
