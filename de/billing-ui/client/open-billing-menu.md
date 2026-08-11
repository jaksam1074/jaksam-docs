---
title: "Rechnungsmenü öffnen"
description: "Öffne das Billing-UI-Menü direkt für ein bekanntes Ziel, ohne dass der Spieler eines anklicken muss."
icon: "file-invoice-dollar"
---

Auslösen, um das Billing-UI-Menü zu öffnen, ohne dass der Spieler den Ziel-Spieler mit der Maus auswählen muss.

```lua Event
TriggerEvent("billing_ui:openBillingMenu", targetServerID)
```

### Parameter

| Name             | Datentyp | Beschreibung                  |
| ----------------- | --------- | -------------------------------- |
| `targetServerID`  | integer   | Ziel-Server-ID, oder `nil`         |

## Beispiel

```lua
local closestPlayer = ESX.Game.GetClosestPlayer()
local targetPlayerId = GetPlayerServerId(closestPlayer)

TriggerEvent("billing_ui:openBillingMenu", targetPlayerId)
```
