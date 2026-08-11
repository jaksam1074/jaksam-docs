---
title: "Fahrzeug repariert"
description: "Wird ausgelöst, nachdem ein Fahrzeug über das Job-Actions-Menü repariert wurde, nützlich für zusätzliche Reparaturlogik."
icon: "wrench"
---

Wird ausgelöst, nachdem ein Fahrzeug über das Job-Actions-Menü repariert wurde. Nützlich, wenn du eine zusätzliche Reparaturfunktion zu den bestehenden hinzufügen möchtest.

```lua Event
AddEventHandler("jobs_creator:vehicleRepaired", function(vehicle)
    -- Hier kannst du die zusätzlichen Reparaturfunktionen hinzufügen
end)
```

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicle` | vehicle handle | Das Handle des Fahrzeugs |
