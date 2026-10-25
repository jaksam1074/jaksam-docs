---
title: "Server"
description: "Server-seitige Hooks und Exports von Boosting Creator: Spieler aus der Warteschlange heraushalten, auf das Ende eines Auftrags reagieren, ein Script-Event abschalten."
icon: "server"
---

## Hooks

Beide Hooks liegen in `integrations/sv_integrations.lua`. Schreibe deinen Code in die Funktionen.

### CanPlayerJoinBoostingQueue

Wird aufgerufen, wenn ein Spieler auf **Anstellen** drückt. Gib `false` zurück, um ihn draußen zu halten, zum Beispiel für eine Gang-Prüfung oder einen eigenen Cooldown.

```lua
function CanPlayerJoinBoostingQueue(playerId)
    return true
end
```

| Parameter | Typ | Beschreibung |
| --- | --- | --- |
| `playerId` | `number` | Server-ID des Spielers |

Polizei-Jobs werden abgelehnt, bevor dieser Hook aufgerufen wird.

### OnBoostingContractEnded

Wird einmal aufgerufen, wenn ein Auftrag endet, egal wie er endet.

```lua
function OnBoostingContractEnded(playerId, contract, outcome, payout)
    if outcome == "delivered" then
        -- give an achievement, a bonus item...
    end
end
```

| Parameter | Typ | Beschreibung |
| --- | --- | --- |
| `playerId` | `number` | Server-ID des Spielers, der den Auftrag angenommen hat (der Crew-Anführer) |
| `contract` | `table` | Der Auftrag: `contract.model`, `contract.plate`, `contract.type` (`dropoff`, `vin`, `chop`, `bulk`), `contract.class.id`, `contract.class.label`, `contract.members` (jedes Mitglied, mit `id` und `name`) |
| `outcome` | `string` | `delivered`, `vin_done`, `stored` (in der Garage des Diebs abgestellt), `failed`, `expired` oder `cancelled` |
| `payout` | `number` | Das Geld, das jedes Mitglied bekommen hat (bei einer Crew der Anteil eines Mitglieds), `0`, wenn nichts gezahlt wurde |

## Exports

### disableScriptEvent

Schaltet einen der eigenen Event-Handler des Scripts ab, um ihn durch deinen zu ersetzen.

```lua
exports["boosting_creator"]:disableScriptEvent(eventName)
```

| Parameter | Typ | Beschreibung |
| --- | --- | --- |
| `eventName` | `string` | Name des abzuschaltenden Events |

## vehicles_keys

Läuft `vehicles_keys`, nutzt Boosting Creator dessen Lockpick und Kurzschließen statt des eigenen Aufbrechens und Kurzschließens. Nichts zu konfigurieren.
