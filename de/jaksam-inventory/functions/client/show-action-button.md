---
title: "Show action button"
description: "Macht einen zuvor versteckten Action Button in der Inventar-UI wieder sichtbar."
icon: "eye"
---

Macht einen zuvor versteckten Action Button in der Inventar-UI wieder sichtbar.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:showActionButton(id)
```

```lua Example
-- Einen als versteckt registrierten Button anzeigen
exports['jaksam_inventory']:showActionButton('police_actions')

-- Anzeigen, wenn der Spieler einen bestimmten Job bekommt
AddEventHandler('esx:setJob', function(job)
    if job.name == 'police' then
        exports['jaksam_inventory']:showActionButton('police_actions')
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `id` | string | Die eindeutige Kennung des anzuzeigenden Buttons |

### Rückgabewert

Keiner.
