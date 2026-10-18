---
title: "Darf stürmen"
description: "Eigene Bedingungen zum Aufbrechen der Tür einer Fälscherwerkstatt hinzufügen."
icon: "building-shield"
---

Wird aufgerufen, wenn ein Beamter beginnt, die Tür einer Werkstatt aufzubrechen. Einheit und Rang, Dienst, genug Beamte online, das Rammbock-Item und die Wartezeit seit der letzten Razzia werden vorher geprüft. Gib `false` zurück, um den Aufbruch zu blockieren.

Bearbeite `Editable.CanRaid` in `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.CanRaid(src, workshopId)
    return true
end
```

```lua Example
-- Raids need a warrant from your MDT
function Editable.CanRaid(src, workshopId)
    return exports["my_mdt"]:HasWarrant("workshop", workshopId)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `src` | integer | Server-ID des Beamten |
| `workshopId` | string | Die Werkstatt-ID, ein Schlüssel von `Config.Forgery.workshops` |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `allowed` | boolean | **true**, um den Aufbruch zu erlauben |
