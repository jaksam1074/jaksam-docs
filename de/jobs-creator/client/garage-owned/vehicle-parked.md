---
title: "Fahrzeug geparkt"
description: "Wird ausgelöst, nachdem ein Fahrzeug aus der Garage der eigenen Fahrzeuge geparkt wurde."
icon: "square-parking"
---

Wird ausgelöst, nachdem das Fahrzeug aus der Garage der eigenen Fahrzeuge geparkt wurde.

```lua Event
AddEventHandler("jobs_creator:garage_owned:vehicleParked", function(vehicleModel, vehiclePlate)
end)
```

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicleModel` | integer | Das Entity-Modell des Fahrzeugs |
| `vehiclePlate` | string | Kennzeichen des Fahrzeugs |
