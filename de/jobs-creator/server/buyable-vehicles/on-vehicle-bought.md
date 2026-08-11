---
title: "Fahrzeug gekauft"
description: "Wird ausgelöst, wenn ein Spieler ein Fahrzeug aus einem kaufbaren Garagen-Marker kauft."
icon: "car"
---

Wird ausgelöst, wenn ein Spieler ein Fahrzeug aus einem kaufbaren Garagen-Marker kauft.

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:permanent_garage:vehicleBought", function(playerId, markerId, vehicleName, vehicleId)
end)
```

```lua Beispiel
RegisterNetEvent("jobs_creator:permanent_garage:vehicleBought", function(playerId, markerId, vehicleName, vehicleId)
    print("Spieler-ID: " .. playerId .. " hat einen " .. vehicleName .. " mit ID " .. vehicleId .. " aus Marker " .. markerId .. " gekauft")
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `markerId` | integer | Marker-ID |
| `vehicleName` | string | Fahrzeugmodellname |
| `vehicleId` | integer | Fahrzeug-ID in der Datenbank |
