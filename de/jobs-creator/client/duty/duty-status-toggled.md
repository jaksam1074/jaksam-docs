---
title: "Duty-Status umgeschaltet"
description: "Wird client-seitig ausgelöst, nachdem der Spieler sich an- oder abmeldet."
icon: "briefcase"
---

Wird client-seitig ausgelöst, nachdem der Spieler sich an-/abmeldet.

<CodeGroup>

```lua Event
AddEventHandler("jobs_creator:toggleDuty", function(isOnDuty)
end)
```

```lua Beispiel
AddEventHandler("jobs_creator:toggleDuty", function(isOnDuty)
    if(isOnDuty) then
        ESX.ShowNotification("You are now on duty")
    else
        ESX.ShowNotification("You are now off duty")
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isOnDuty` | boolean | Neuer Duty-Status des Spielers |
