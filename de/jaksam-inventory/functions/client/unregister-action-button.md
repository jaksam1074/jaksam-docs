---
title: "Unregister action button"
description: "Entfernt einen zuvor registrierten Action Button aus der Inventar-UI."
icon: "square-minus"
---

Entfernt einen zuvor registrierten Action Button aus der Inventar-UI.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterActionButton(id)
```

```lua Example
-- Einen Button entfernen, wenn er nicht mehr gebraucht wird
exports['jaksam_inventory']:unregisterActionButton('my_custom_button')

-- Entfernen, wenn der Spieler den Job verlässt
AddEventHandler('esx:setJob', function(job)
    if job.name ~= 'police' then
        exports['jaksam_inventory']:unregisterActionButton('police_actions')
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `id` | string | Die eindeutige Kennung des zu entfernenden Buttons (gleiche ID wie bei `registerActionButton`) |

### Rückgabewert

Keiner.
