---
title: "Set weapon wheel"
description: "Aktiviert oder deaktiviert das Standard-GTA5-Waffenrad und zugehörige Waffeneinstellungen. Nützlich für Minigames."
icon: "circle-dot"
---

Aktiviert oder deaktiviert das Waffenrad und zugehörige Waffeneinstellungen. Nützlich für Minigames, in denen du das GTA-5-Waffenrad willst.

<Warning>
  Diese Funktion verhindert die Nutzung von Waffen aus dem Inventar, sie ist hauptsächlich für FFA-Minigames gedacht.
</Warning>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:setWeaponWheel(state)
```

```lua Example
-- GTA5-Waffenrad deaktivieren (Standard-jaksam_inventory-Modus)
exports['jaksam_inventory']:setWeaponWheel(false)

-- GTA5-Waffenrad aktivieren (nur für Minigames aktivieren)
exports['jaksam_inventory']:setWeaponWheel(true)

-- Standard-GTA5-Waffenrad während eines FFA-Minigames aktivieren
exports['jaksam_inventory']:setWeaponWheel(true)
-- ... Minigame-Code ...
exports['jaksam_inventory']:setWeaponWheel(false) -- GTA5-Rad wieder deaktivieren, zurück zu normalem jaksam_inventory
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `state` | boolean \| nil | Bei true wird das Standard-GTA5-Waffenrad aktiviert und Waffen werden NICHT von jaksam inventory verwaltet. Bei false wird das Standard-GTA5-Waffenrad deaktiviert und Waffen WERDEN von jaksam inventory verwaltet. Bei nil wird der aktuelle interne Zustand verwendet |

### Rückgabewert

Keiner. Legt beim Aufruf automatisch die aktuelle Waffe ab.
