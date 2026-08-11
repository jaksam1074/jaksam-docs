---
title: "Spieler entlassen"
description: "Wird ausgelöst, wenn ein Spieler aus einem Job entlassen wurde."
icon: "user-xmark"
---

Wird ausgelöst, wenn ein Spieler aus einem Job entlassen wurde.

```lua Event
RegisterNetEvent("jobs_creator:boss:employeeFired", function(employeeIdentifier, jobName)
end)
```

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `employeeIdentifier` | string | Charakter-Identifier des Spielers |
| `jobName` | string | Die Job-ID, aus der der Spieler entlassen wurde |
