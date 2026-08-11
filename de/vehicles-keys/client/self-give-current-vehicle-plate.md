---
title: "Aktuelles Fahrzeug-Kennzeichen selbst geben"
description: "Gib dir selbst die Schlüssel des Fahrzeugs, das du gerade fährst, ohne dessen Kennzeichen zu benötigen."
icon: "car-side"
---

Dieses Event macht dasselbe wie [Fahrzeug-Kennzeichen selbst geben](/de/vehicles-keys/client/self-give-vehicle-plate), ist aber noch einfacher, da es keinen Parameter benötigt — es ist einfach eine Copy-Paste-Zeile.

Das Auslösen dieses Events findet automatisch das Fahrzeug, das der lokale Spieler fährt, und gibt ihm dessen Schlüssel.

```lua Event
TriggerServerEvent("vehicles_keys:selfGiveCurrentVehicleKeys")
```

## Beispiel

```lua
-- Nur ein Event eines imaginären Fahrschul-Scripts
RegisterNetEvent("driving_school:test_started", function()
    local vehicle = CreateVehicle("blista", 249.40, -1407.23, 30.40, true, false)
    SetVehicleColours(vehicle, 4, 5)
    SetVehicleExtraColours(vehicle, 1, 2)
    SetEntityHeading(vehicle, 317.64)
    SetVehicleOnGroundProperly(vehicle)
    SetPedIntoVehicle(PlayerPedId(), vehicle, -1)

    -- VEHICLES KEYS INTEGRATION, UM DIE SCHLÜSSEL EINFACH ZU GEBEN
    TriggerServerEvent("vehicles_keys:selfGiveCurrentVehicleKeys")
end)
```
