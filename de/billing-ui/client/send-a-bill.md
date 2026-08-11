---
title: "Rechnung senden"
description: "Sende eine Rechnung an einen Ziel-Spieler."
icon: "paper-plane"
---

Auslösen, um eine Rechnung an einen Ziel-Spieler zu senden.

```lua Event
TriggerServerEvent("billing_ui:sendBill", targetId, societyName, reason, amount)
```

### Parameter

| Name          | Datentyp | Beschreibung                                                    |
| ------------- | --------- | ------------------------------------------------------------------ |
| `targetId`    | integer   | Server-ID des Ziel-Spielers                                              |
| `societyName` | string    | Name der Society (erhält das Geld aus der bezahlten Rechnung)          |
| `reason`      | string    | Der Grund der Rechnung                                             |
| `amount`      | integer   | Der Betrag der Rechnung                                             |

## Beispiel

```lua
local closestPlayer, closestDist = ESX.Game.GetClosestPlayer()
local targetId = GetPlayerServerId(closestPlayer)
local societyName = "society_police"
local reason = "Speed limit"
local amount = 500

TriggerServerEvent("billing_ui:sendBill", targetId, societyName, reason, amount)
```
