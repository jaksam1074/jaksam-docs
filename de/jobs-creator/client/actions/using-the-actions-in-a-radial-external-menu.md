---
title: "Actions in externen Menüs"
description: "Löse Jobs-Creator-Actions über beliebige externe oder Radial-Menüs mithilfe von client-seitigen Events aus."
icon: "circle-dot"
---

Du kannst die Actions in jedem externen Menü verwenden. Hier sind die Trigger, die du in externen Scripts verwenden kannst.

<Warning>
  Stelle sicher, dass die Actions für den Job in den Jobs-Creator-Einstellungen dieses Jobs aktiviert sind, um Probleme zu vermeiden. Du kannst die Actions selbst aktivieren, während du **"Can open actions menu"** deaktivierst.
</Warning>

## Identität prüfen

```lua
-- Trigger, um die Check-Identity-Action zu starten
TriggerEvent("jobs_creator:actions:checkIdentity")
```

## Fahrzeughalter prüfen

```lua
-- Trigger, um die Check-Vehicle-Owner-Action zu starten
TriggerEvent("jobs_creator:actions:checkVehicleOwner")
```

## Rechnung erstellen

```lua
-- Trigger, um die Billing-Action zu starten
TriggerEvent("jobs_creator:actions:createBilling")
```

## Spieler schleifen

```lua
-- Trigger, um die Drag-Action zu starten
TriggerEvent("jobs_creator:actions:drag")
```

## Spieler fesseln

```lua
-- Trigger, um die Soft-Handcuff-Action zu starten
TriggerEvent("jobs_creator:actions:softHandcuff")
-- Trigger, um die Hard-Handcuff-Action zu starten
TriggerEvent("jobs_creator:actions:hardHandcuff")
```

## Heal big

```lua
-- Trigger, um die Heal-Big-Action zu starten
TriggerEvent("jobs_creator:actions:healBig")
```

## Heal small

```lua
-- Trigger, um die Heal-Small-Action zu starten
TriggerEvent("jobs_creator:actions:healSmall")
```

## Impound

```lua
-- Trigger, um die Impound-Action zu starten
TriggerEvent("jobs_creator:actions:impoundVehicle")
```

## Lizenzen-Menü

```lua
-- Trigger, um das Lizenzen-Menü anzuzeigen
TriggerEvent("jobs_creator:actions:checkLicenses")
```

## Auto aufbrechen

```lua
-- Trigger, um die Lockpick-Car-Action zu starten
TriggerEvent("jobs_creator:actions:lockpickCar")
```

## In Auto setzen

```lua
-- Trigger, um die Put-In-Car-Action zu starten
TriggerEvent("jobs_creator:actions:putInCar")
```

## Aus Auto holen

```lua
-- Trigger, um die Take-From-Car-Action zu starten
TriggerEvent("jobs_creator:actions:takeFromCar")
```

## Fahrzeug reparieren

```lua
-- Trigger, um die Repair-Vehicle-Action zu starten
TriggerEvent("jobs_creator:actions:repairVehicle")
```

## Wiederbeleben

```lua
-- Trigger, um die Revive-Action zu starten
TriggerEvent("jobs_creator:actions:revive")
```

## Durchsuchen

```lua
-- Trigger, um die Search-Action zu starten
TriggerEvent("jobs_creator:actions:search")
```

## Fahrzeug waschen

```lua
-- Trigger, um die Wash-Vehicle-Action zu starten
TriggerEvent("jobs_creator:actions:washVehicle")
```

## Platzierbare-Objekte-Menü öffnen

```lua
-- Trigger, um das Platzierbare-Objekte-Menü zu öffnen
TriggerEvent("jobs_creator:actions:placeObject")
```
