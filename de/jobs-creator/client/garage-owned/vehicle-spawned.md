---
title: "Fahrzeug gespawnt"
description: "Wird ausgelöst, nachdem ein Fahrzeug aus der Garage der eigenen Fahrzeuge gespawnt wird."
icon: "car"
---

Wird ausgelöst, nachdem ein Fahrzeug aus der Garage der eigenen Fahrzeuge gespawnt wurde.

<CodeGroup>

```lua Event
AddEventHandler("jobs_creator:garage_owned:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)
end)
```

```lua Beispiel
AddEventHandler("jobs_creator:garage_owned:vehicleSpawned", function(vehicle, vehicleName, vehiclePlate)
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
