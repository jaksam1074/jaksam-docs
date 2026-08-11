---
title: "Externes Impound-Script integrieren"
description: "Binde dein eigenes Impound-Script in Jobs Creator ein, wenn ein Fahrzeug abgeschleppt wird."
icon: "warehouse"
---

Wird ausgelöst, wenn ein Fahrzeug abgeschleppt wird.

<CodeGroup>

```lua Event
AddEventHandler("jobs_creator:actions:vehicleImpounded", function(vehiclePlate, vehicleModel)
end)
```

```lua Beispiel
RegisterNetEvent("jobs_creator:actions:vehicleImpounded", function(vehiclePlate, vehicleModel)
    -- Hier kannst du die Exports deines Impound-Scripts hinzufügen
    TriggerServerEvent("impound_script:impoundVehicle", vehiclePlate, vehicleModel)
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehiclePlate` | string | Das Kennzeichen des Fahrzeugs |
| `vehicleModel` | string | Das Modell des Fahrzeugs |
