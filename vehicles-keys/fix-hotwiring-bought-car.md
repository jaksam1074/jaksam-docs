---
title: "Fix hotwiring bought car"
description: "Refresh a player's owned vehicles after a purchase so they don't have to hotwire it, for common vehicle shop scripts."
icon: "wrench"
---

## Generic script

If you have to hotwire a vehicle right after purchasing it, add [this simple line of code](/vehicles-keys/client/refresh-self-owned-vehicles) to your script, after the vehicle has been added to the `owned_vehicles` / `player_vehicles` table (depending on the framework).

You may want to add a `Citizen.Wait(2000)` before that line, in case the vehicle wasn't yet in the table at the moment you triggered the event.

## esx_vehicleshop

### First step

Go to `esx_vehicleshop/server/main.lua` and search for the following code:

<Frame>
  ![esx_vehicleshop setVehicleOwnedPlayerId before](/images/esx_vehicleshop_setVehicleOwnedPlayerId_before.png)
</Frame>

And add this line:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
```

<Frame>
  ![esx_vehicleshop setVehicleOwnedPlayerId after](/images/esx_vehicleshop_setVehicleOwnedPlayerId_after.png)
</Frame>

### Second step

Go to `esx_vehicleshop/server/main.lua` (the same file as before) and search for the following code:

<Frame>
  ![esx_vehicleshop buyVehicle before](/images/esx_vehicleshop_buyVehicle_before.png)
</Frame>

And add this line:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(source)
```

<Frame>
  ![esx_vehicleshop buyVehicle after](/images/esx_vehicleshop_buyVehicle_after.png)
</Frame>

## esx_advancedvehicleshop

Go to `esx_advancedvehicleshop/server/main.lua` and search for the following code:

<Frame>
  ![esx_advancedvehicleshop before](/images/esx_advancedvehicleshop_before.png)
</Frame>

And add this line:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(source)
```

<Frame>
  ![esx_advancedvehicleshop after](/images/esx_advancedvehicleshop_after.png)
</Frame>

## qb-vehicleshop

### First step

Go to `qb-vehicleshop/server.lua` and add the following code after **all** `exports.oxmysql:insert` calls.

<Note>
  In the example it's shown only once, but you have to add it multiple times.
</Note>

<Frame>
  ![qb-vehicleshop before](/images/qb-vehicleshop_before.png)
</Frame>

Add the following code:

```lua
SetTimeout(1000, function()
    exports["vehicles_keys"]:refreshPlayerOwnedVehicles( pData.PlayerData.source )
end)
```

In certain parts, you'll have to replace `pData` with something else. Here it shows where to add the code and what `pData` depends on.

<Frame>
  ![qb-vehicleshop after](/images/qb-vehicleshop_after.png)
</Frame>

<Note>
  The green circles shown in the screenshot must match — so if the first one is, for example, `targetPlayer`, the second one must be `targetPlayer` as well.
</Note>

### Second step

Go to `qb-vehicleshop/server.lua` (the same file as before) and replace all these events (they're at the bottom of the file):

```lua
TriggerClientEvent('vehiclekeys:client:SetOwner', buyerId, plate)
```

with the following code:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(buyerId)
```

## okokVehicleShop

Go to `okokVehicleShop/sv_utils.lua` and search for the following code:

<Frame>
  ![okokVehicleShop before](/images/okokVehicleShop_before.png)
</Frame>

And add this line:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(_source)
```

<Frame>
  ![okokVehicleShop after](/images/okokVehicleShop_after.png)
</Frame>

## s4-vehicleshop

Go to `s4-vehicleshop/server.lua` and search for the following code:

<Frame>
  ![s4-vehicleshop before](/images/s4-vehicleshop_before.png)
</Frame>

And add the following code:

```lua
SetTimeout(1000, function()
    exports["vehicles_keys"]:refreshPlayerOwnedVehicles(src)
end)
```

<Frame>
  ![s4-vehicleshop after](/images/s4-vehicleshop_after.png)
</Frame>

<Note>
  This code works for both _oxmysql_ and _ghmattimysql_ versions.
</Note>

## t1ger_dealerships

### First step

Go to `t1ger_dealerships/server/main.lua` and add the following line below **all** occurrences (more than one) of the code shown in the example:

```lua
exports['t1ger_keys']:UpdateKeysToDatabase(props.plate, true)
```

<Frame>
  ![t1ger_dealerships before](/images/t1ger_dealerships_before.png)
</Frame>

Add the following line:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(xPlayer.source)
```

<Frame>
  ![t1ger_dealerships after](/images/t1ger_dealerships_after.png)
</Frame>

### Second step

Go to `t1ger_dealerships/server/main.lua` (the same file as before) and search for the following code:

<Frame>
  ![t1ger_dealerships2 before](/images/t1ger_dealerships2_before.png)
</Frame>

Add the following line:

```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(xPlayer.source)
```

<Frame>
  ![t1ger_dealerships2 after](/images/t1ger_dealerships2_after.png)
</Frame>
