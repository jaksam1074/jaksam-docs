---
title: "Fahrzeug geparkt"
description: "Wird ausgelöst, nachdem ein Fahrzeug aus der Buyable-Vehicles-Garage geparkt wurde."
icon: "car"
---

Wird ausgelöst, nachdem das Fahrzeug aus der Buyable-Vehicles-Garage geparkt wurde.

```lua Event
AddEventHandler("jobs_creator:permanent_garage:vehicleParked", function(vehicleModel, vehiclePlate)
end)
```

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicleModel` | integer | Das Entity-Modell des Fahrzeugs |
| `vehiclePlate` | string | Kennzeichen des Fahrzeugs |
