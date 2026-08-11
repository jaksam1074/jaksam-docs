---
title: "Aktuellen Duty-Status umschalten"
description: "Trigger, um den aktuellen Duty-Status des Spielers umzuschalten oder explizit zu setzen."
icon: "briefcase"
---

Trigger, um den aktuellen Duty-Status des Spielers umzuschalten.

## Umschalten

Dies schaltet den aktuellen Duty-Status des Spielers um (war er offline, geht er auf Duty, und umgekehrt).

<CodeGroup>

```lua Event
TriggerEvent("jobs_creator:toggleCurrentDutyStatus")
```

```lua Beispiel
-- Schaltet den aktuellen Duty-Status um
RegisterCommand("duty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus")
end, false)
```

</CodeGroup>

## Explizit setzen

Dies setzt den Duty-Status des Spielers auf den angegebenen Status, anstatt ihn umzuschalten.

<CodeGroup>

```lua Event
TriggerEvent("jobs_creator:toggleCurrentDutyStatus", newDutyStatus)
```

```lua Beispiel
RegisterCommand("onduty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus", true)
end, false)
RegisterCommand("offduty", function()
    TriggerEvent("jobs_creator:toggleCurrentDutyStatus", false)
end, false)
```

</CodeGroup>
