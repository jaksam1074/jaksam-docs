---
title: "Bei Razzia"
description: "Einen Dispatch-Ruf oder deinen eigenen Alarm senden, wenn eine Razzia auf eine Fälscherwerkstatt weitergeht."
icon: "tower-broadcast"
---

Wird jedes Mal aufgerufen, wenn eine Razzia weitergeht. Hier gehört dein Dispatch-Ruf oder dein eigener Alarm hin.

Bearbeite `Editable.OnRaid` in `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.OnRaid(workshopId, phase, src)

end
```

```lua Example
function Editable.OnRaid(workshopId, phase, src)
    if phase == "breach" then
        local workshop = Config.Forgery.workshops[workshopId]
        exports["my_dispatch"]:Alert({
            job = "police",
            title = "Raid in progress",
            message = ("Officers are breaching %s"):format(workshop and workshop.label or workshopId),
            coords = src and GetEntityCoords(GetPlayerPed(src)),
        })
    end
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `workshopId` | string | Die Werkstatt-ID, ein Schlüssel von `Config.Forgery.workshops` (im Spiel hinzugefügte Werkstätten sind auch dort) |
| `phase` | string | `breach` (ein Beamter hat begonnen, die Tür aufzubrechen), `aborted` (der Aufbruch wurde aufgegeben), `open` (die Tür hat nachgegeben, die Beamten können hinein), `over` (die Razzia ist vorbei, die Werkstatt ist versiegelt) |
| `src` | integer \| nil | Server-ID des Beamten, der es getan hat, **nil**, wenn die Zeit abgelaufen ist oder ein Admin es getan hat |
