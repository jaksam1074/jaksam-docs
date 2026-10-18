---
title: "Darf Werkstatt betreten"
description: "Eigene Bedingungen zum Betreten einer Fälscherwerkstatt hinzufügen."
icon: "door-open"
---

Wird aufgerufen, wenn ein Spieler eine Fälscherwerkstatt betritt. Dass der Spieler Mitglied des besitzenden Jobs ist, ab dem `minGrade` der Werkstatt, wird vorher geprüft. Gib `false` zurück, um ihn draußen zu lassen.

Bearbeite `Editable.CanEnterWorkshop` in `editable/server.lua`:

<CodeGroup>

```lua Function
function Editable.CanEnterWorkshop(src, workshopId)
    return true
end
```

```lua Example
-- Nobody enters while wanted by the police
function Editable.CanEnterWorkshop(src, workshopId)
    return not exports["my_wanted"]:IsWanted(src)
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `src` | integer | Server-ID des Spielers |
| `workshopId` | string | Die Werkstatt-ID, ein Schlüssel von `Config.Forgery.workshops` |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `allowed` | boolean | **true**, um den Spieler hereinzulassen |
