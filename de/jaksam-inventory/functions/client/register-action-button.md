---
title: "Register action button"
description: "Registriert einen eigenen Action Button in der Inventar-UI-Toolbar."
icon: "square-plus"
---

Registriert einen eigenen Action Button in der Inventar-UI-Toolbar. Action Buttons erscheinen auf der rechten Seite des Inventars und können beim Klicken beliebige eigene Logik auslösen.

<Tip>
  Eine vollständige Anleitung mit Bildern und Beispielen findest du im [Action-Buttons-Guide](/de/jaksam-inventory/guides/action-buttons).
</Tip>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerActionButton(id, icon, tooltip, onClick, visible)
```

```lua Example
-- Einen einfachen Action Button registrieren
exports['jaksam_inventory']:registerActionButton(
    'my_custom_button',
    'bi-star-fill',
    'My Custom Action',
    function()
        print('Button clicked!')
        -- Deine eigene Logik hier
    end
)

-- Einen versteckten Button registrieren (später basierend auf Bedingungen anzeigen)
exports['jaksam_inventory']:registerActionButton(
    'police_actions',
    'bi-shield-check',
    'Police Actions',
    function()
        TriggerEvent('myPoliceScript:openMenu')
    end,
    false -- standardmäßig versteckt
)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `id` | string | Eindeutige Kennung für den Button. Wird zum Referenzieren beim Anzeigen/Verstecken/Entregistrieren genutzt |
| `icon` | string | Bootstrap-Icons-Klassenname (z.B. "bi-shield-x", "bi-car-front-fill"). Icons unter [icons.getbootstrap.com](https://icons.getbootstrap.com/) finden |
| `tooltip` | string \| nil | Tooltip-Text beim Hovern über den Button. Kann nil sein für keinen Tooltip |
| `onClick` | function | Callback-Funktion, die beim Klicken des Buttons ausgeführt wird |
| `visible` | boolean \| nil | Ob der Button anfangs sichtbar sein soll. Standard: true |

### Rückgabewert

Keiner.
