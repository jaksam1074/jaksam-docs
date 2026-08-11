---
title: "Fahrzeug geparkt"
description: "Wird ausgelöst, nachdem ein Fahrzeug aus der temporären Garage geparkt wurde."
icon: "square-parking"
---

Wird ausgelöst, nachdem das Fahrzeug aus der temporären Garage geparkt wurde.

```lua Event
AddEventHandler("jobs_creator:temporary_garage:vehicleParked", function(vehicleModel, vehiclePlate)
end)
```

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicleModel` | integer | Das Entity-Modell des Fahrzeugs |
| `vehiclePlate` | string | Kennzeichen des Fahrzeugs |
