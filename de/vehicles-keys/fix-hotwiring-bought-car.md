---
title: "Kurzschließen bei gekauftem Fahrzeug beheben"
description: "Die Fahrzeuge eines Spielers nach einem Kauf aktualisieren, damit er es nicht kurzschließen muss, für gängige Fahrzeug-Shop-Scripts."
icon: "wrench"
---

## Generisches Script

Musst du ein Fahrzeug direkt nach dem Kauf kurzschließen, füge [diese einfache Codezeile](/de/vehicles-keys/client/refresh-self-owned-vehicles) zu deinem Script hinzu, nachdem das Fahrzeug zur Tabelle `owned_vehicles` / `player_vehicles` (je nach Framework) hinzugefügt wurde.

Eventuell willst du davor ein `Citizen.Wait(2000)` einfügen, falls das Fahrzeug zum Zeitpunkt des Event-Triggers noch nicht in der Tabelle war.

## esx_vehicleshop

### Erster Schritt

Gehe zu `esx_vehicleshop/server/main.lua` und suche nach folgendem Code:

<Frame>
  ![esx_vehicleshop setVehicleOwnedPlayerId before](/images/esx_vehicleshop_setVehicleOwnedPlayerId_before.png)
</Frame>

Und füge diese Zeile hinzu:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
```

<Frame>
  ![esx_vehicleshop setVehicleOwnedPlayerId after](/images/esx_vehicleshop_setVehicleOwnedPlayerId_after.png)
</Frame>

### Zweiter Schritt

Gehe zu `esx_vehicleshop/server/main.lua` (die gleiche Datei wie zuvor) und suche nach folgendem Code:

<Frame>
  ![esx_vehicleshop buyVehicle before](/images/esx_vehicleshop_buyVehicle_before.png)
</Frame>

Und füge diese Zeile hinzu:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(source)
```

<Frame>
  ![esx_vehicleshop buyVehicle after](/images/esx_vehicleshop_buyVehicle_after.png)
</Frame>

## esx_advancedvehicleshop

Gehe zu `esx_advancedvehicleshop/server/main.lua` und suche nach folgendem Code:

<Frame>
  ![esx_advancedvehicleshop before](/images/esx_advancedvehicleshop_before.png)
</Frame>

Und füge diese Zeile hinzu:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(source)
```

<Frame>
  ![esx_advancedvehicleshop after](/images/esx_advancedvehicleshop_after.png)
</Frame>

## qb-vehicleshop

### Erster Schritt

Gehe zu `qb-vehicleshop/server.lua` und füge folgenden Code nach **allen** `exports.oxmysql:insert`-Aufrufen hinzu.

<Note>
  Im Beispiel wird es nur einmal gezeigt, du musst es aber mehrfach hinzufügen.
</Note>

<Frame>
  ![qb-vehicleshop before](/images/qb-vehicleshop_before.png)
</Frame>

Füge folgenden Code hinzu:

```lua
SetTimeout(1000, function()
    exports["vehicles_keys"]:refreshPlayerOwnedVehicles( pData.PlayerData.source )
end)
```

An manchen Stellen musst du `pData` durch etwas anderes ersetzen. Hier siehst du, wo der Code hinkommt und wovon `pData` abhängt.

<Frame>
  ![qb-vehicleshop after](/images/qb-vehicleshop_after.png)
</Frame>

<Note>
  Die grünen Kreise im Screenshot müssen übereinstimmen, ist der erste zum Beispiel `targetPlayer`, muss der zweite auch `targetPlayer` sein.
</Note>

### Zweiter Schritt

Gehe zu `qb-vehicleshop/server.lua` (die gleiche Datei wie zuvor) und ersetze alle diese Events (sie stehen am Ende der Datei):

```lua
TriggerClientEvent('vehiclekeys:client:SetOwner', buyerId, plate)
```

durch folgenden Code:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(buyerId)
```

## okokVehicleShop

Gehe zu `okokVehicleShop/sv_utils.lua` und suche nach folgendem Code:

<Frame>
  ![okokVehicleShop before](/images/okokVehicleShop_before.png)
</Frame>

Und füge diese Zeile hinzu:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(_source)
```

<Frame>
  ![okokVehicleShop after](/images/okokVehicleShop_after.png)
</Frame>

## s4-vehicleshop

Gehe zu `s4-vehicleshop/server.lua` und suche nach folgendem Code:

<Frame>
  ![s4-vehicleshop before](/images/s4-vehicleshop_before.png)
</Frame>

Und füge folgenden Code hinzu:

```lua
SetTimeout(1000, function()
    exports["vehicles_keys"]:refreshPlayerOwnedVehicles(src)
end)
```

<Frame>
  ![s4-vehicleshop after](/images/s4-vehicleshop_after.png)
</Frame>

<Note>
  Dieser Code funktioniert sowohl für _oxmysql_ als auch für _ghmattimysql_.
</Note>

## t1ger_dealerships

### Erster Schritt

Gehe zu `t1ger_dealerships/server/main.lua` und füge folgende Zeile unterhalb **aller** Vorkommen (mehr als eins) des im Beispiel gezeigten Codes hinzu:

```lua
exports['t1ger_keys']:UpdateKeysToDatabase(props.plate, true)
```

<Frame>
  ![t1ger_dealerships before](/images/t1ger_dealerships_before.png)
</Frame>

Füge folgende Zeile hinzu:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(xPlayer.source)
```

<Frame>
  ![t1ger_dealerships after](/images/t1ger_dealerships_after.png)
</Frame>

### Zweiter Schritt

Gehe zu `t1ger_dealerships/server/main.lua` (die gleiche Datei wie zuvor) und suche nach folgendem Code:

<Frame>
  ![t1ger_dealerships2 before](/images/t1ger_dealerships2_before.png)
</Frame>

Füge folgende Zeile hinzu:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(xPlayer.source)
```

<Frame>
  ![t1ger_dealerships2 after](/images/t1ger_dealerships2_after.png)
</Frame>
