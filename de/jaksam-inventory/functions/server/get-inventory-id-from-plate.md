---
title: "Get inventory ID from plate"
description: "Löst die vollständige Inventar-ID für eine Fahrzeugabteilung nur anhand des Kennzeichens auf."
icon: "id-card"
---

Löst die vollständige Inventar-ID für eine Fahrzeugabteilung nur anhand des Kennzeichens auf.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getInventoryIdFromPlate(plate, compartment)
```

```lua Example
-- Kofferraum-Inventar-ID abrufen
local plate = GetVehicleNumberPlateText(vehicle)
local trunkId = exports['jaksam_inventory']:getInventoryIdFromPlate(plate, "trunk")

if trunkId then
    print("Trunk ID: " .. trunkId)
    -- Jetzt kannst du die Standard-Inventarfunktionen nutzen
    local inventory = exports['jaksam_inventory']:getInventory(trunkId)
end

-- Handschuhfach-Inventar-ID abrufen
local gloveboxId = exports['jaksam_inventory']:getInventoryIdFromPlate("ABC 123", "glovebox")
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `plate` | string | Das Fahrzeugkennzeichen |
| `compartment` | string | Entweder "trunk" oder "glovebox" |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string \| nil | Die vollständige Inventar-ID (Format: `"vehicle:plate:model:compartment"`), nil falls das Fahrzeug nicht gefunden wurde |

### Hinweise

Sucht in dieser Reihenfolge:

1. Datenbank der eigenen Fahrzeuge (ESX: `owned_vehicles`, QBCore: `player_vehicles`)
2. Bestehende Inventare in der `jaksam_inventory`-Tabelle
3. Aktuell gespawnte Fahrzeuge (`GetAllVehicles`, NPC-Fahrzeuge)

Bei eigenen Fahrzeugen wird bei Bedarf automatisch ein Inventar erstellt. Erstellte Inventare sind bei eigenen Fahrzeugen persistent, bei NPC-Fahrzeugen temporär. Funktioniert auch, wenn das Fahrzeug aktuell nicht gespawnt ist (Garage).
