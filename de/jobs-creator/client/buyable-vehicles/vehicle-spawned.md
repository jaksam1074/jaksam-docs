---
title: "Fahrzeug gespawnt"
description: "Wird ausgelöst, nachdem ein gekauftes Fahrzeug aus der Buyable-Vehicles-Garage gespawnt wird."
icon: "car"
---

Wird ausgelöst, nachdem ein gekauftes Fahrzeug aus der Buyable-Vehicles-Garage gespawnt wurde.

<CodeGroup>

```lua Event
AddEventHandler("jobs_creator:permanent_garage:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)
end)
```

```lua Beispiel
AddEventHandler("jobs_creator:permanent_garage:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)
    -- Beispiel, um dem Fahrzeug Schlüssel zu geben (du kannst dafür einen eigenen TriggerEvent verwenden)
    giveKeysToVehicle(vehicle)
    print(vehicleName) -- Beispielausgabe 'adder'
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicle` | vehicle handle | Das Handle des Fahrzeugs |
| `vehicleName` | string | Der Name des Fahrzeugs |
| `vehiclePlate` | string | Kennzeichen des Fahrzeugs |
