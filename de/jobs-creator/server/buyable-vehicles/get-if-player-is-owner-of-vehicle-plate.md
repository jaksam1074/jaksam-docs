---
title: "Prüfen, ob Spieler Kennzeichenhalter ist"
description: "Prüfe, ob ein bestimmter Spieler der Halter eines bestimmten Kennzeichens ist."
icon: "drivers-license"
---

Gibt zurück, ob eine Spieler-ID der Halter eines bestimmten Kennzeichens ist.

<CodeGroup>

```lua Export
exports["jobs_creator"]:isPlayerOwnerOfVehiclePlate(playerId, plate)
```

```lua Beispiel
local playerId = 1
local plate = "40PQB261"
local isTheVehicleOwner = exports["jobs_creator"]:isPlayerOwnerOfVehiclePlate(playerId, plate)
print("Ist der Spieler Halter dieses Kennzeichens: " .. tostring(isTheVehicleOwner))
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |
| `plate` | string | Kennzeichen des Fahrzeugs |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isOwner` | boolean | Ob der Spieler der Fahrzeughalter ist oder nicht |
