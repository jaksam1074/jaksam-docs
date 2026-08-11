---
title: "Get vehicle inventory limits"
description: "Gibt die Kofferraum- oder Handschuhfach-Limits für ein Fahrzeug basierend auf dem Modell zurück."
icon: "car"
---

Gibt die Kofferraum- oder Handschuhfach-Limits für ein Fahrzeug basierend auf dem Modell zurück. Nutzt die Konfiguration aus `_data/vehicles.lua` mit der Priorität: `trunkByModel`/`gloveboxByModel` > `trunkByClass`/`gloveboxByClass`. Gibt `0, 0` zurück, falls das Fahrzeug/die Klasse so konfiguriert ist, dass kein Kofferraum/Handschuhfach existiert (`noTrunkVehicles`, `noTrunkClasses`, usw.)

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getVehicleInventoryLimits(vehicleModel, inventoryType)
```

```lua Example
local vehicle = GetVehiclePedIsIn(PlayerPedId(), false)
local maxSlots, maxWeight = exports['jaksam_inventory']:getVehicleInventoryLimits(GetEntityModel(vehicle), "trunk")

if maxWeight then
    print("Trunk max weight: " .. maxWeight)
else
    print("No specific config for this vehicle model/class")
end

-- Handschuhfach-Limits für das Fahrzeug 'adder' abrufen
local gloveboxSlots, gloveboxWeight = exports['jaksam_inventory']:getVehicleInventoryLimits('adder', "glovebox")
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `vehicleModel` | number \| string | Der Fahrzeugmodell-Hash (von `GetEntityModel`) oder der Modellname als String |
| `inventoryType` | string | Entweder `"trunk"` oder `"glovebox"` |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `maxSlots` | number \| nil | Die maximale Slot-Anzahl für das Fahrzeuginventar, oder nil falls keine Konfiguration gefunden wurde |
| `maxWeight` | number \| nil | Das maximale Gewicht für das Fahrzeuginventar, oder nil falls keine Konfiguration gefunden wurde |

### Hinweise

In der Quelldokumentation fehlte im Originalbeispiel ein Komma zwischen `'adder'` und `"glovebox"`, hier korrigiert. Es lohnt sich zu prüfen, ob das auch ein Bug im zugrunde liegenden Script selbst war.
