---
title: "Hide action button"
description: "Versteckt einen Action Button in der Inventar-UI, ohne ihn zu entfernen."
icon: "eye-slash"
---

Versteckt einen Action Button in der Inventar-UI, ohne ihn zu entfernen.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:hideActionButton(id)
```

```lua Example
-- Einen Button vorübergehend verstecken
exports['jaksam_inventory']:hideActionButton('police_actions')

-- Verstecken, wenn der Spieler nicht im Dienst ist
AddEventHandler('esx:setJob', function(job)
    if job.name ~= 'police' then
        exports['jaksam_inventory']:hideActionButton('police_actions')
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `id` | string | Die eindeutige Kennung des zu versteckenden Buttons |

### Rückgabewert

Keiner.
