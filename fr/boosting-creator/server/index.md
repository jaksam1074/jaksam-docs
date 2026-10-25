---
title: "Serveur"
description: "Hooks et exports côté serveur de Boosting Creator : empêche des joueurs de rejoindre la file, réagis quand un contrat se termine, désactive un event du script."
icon: "server"
---

## Hooks

Les deux hooks sont dans `integrations/sv_integrations.lua`. Écris ton code dans les fonctions.

### CanPlayerJoinBoostingQueue

Appelé quand un joueur appuie sur **Rejoindre la file**. Retourne `false` pour l'en empêcher, par exemple pour une vérification de gang ou un cooldown à toi.

```lua
function CanPlayerJoinBoostingQueue(playerId)
    return true
end
```

| Paramètre | Type | Description |
| --- | --- | --- |
| `playerId` | `number` | ID serveur du joueur |

Les jobs de police sont refusés avant l'appel de ce hook.

### OnBoostingContractEnded

Appelé une fois quand un contrat se termine, quelle que soit la façon dont il se termine.

```lua
function OnBoostingContractEnded(playerId, contract, outcome, payout)
    if outcome == "delivered" then
        -- give an achievement, a bonus item...
    end
end
```

| Paramètre | Type | Description |
| --- | --- | --- |
| `playerId` | `number` | ID serveur du joueur qui a accepté le contrat (le chef de l'équipe) |
| `contract` | `table` | Le contrat : `contract.model`, `contract.plate`, `contract.type` (`dropoff`, `vin`, `chop`, `bulk`), `contract.class.id`, `contract.class.label`, `contract.members` (chaque membre, avec `id` et `name`) |
| `outcome` | `string` | `delivered`, `vin_done`, `stored` (gardée dans le garage du voleur), `failed`, `expired` ou `cancelled` |
| `payout` | `number` | L'argent reçu par chaque membre (avec une équipe, la part d'un membre), `0` quand il n'a rien payé |

## Exports

### disableScriptEvent

Désactive un des event handlers du script, pour le remplacer par le tien.

```lua
exports["boosting_creator"]:disableScriptEvent(eventName)
```

| Paramètre | Type | Description |
| --- | --- | --- |
| `eventName` | `string` | Nom de l'event à désactiver |

## vehicles_keys

Quand `vehicles_keys` est démarré, Boosting Creator utilise son crochetage et son démarrage aux fils au lieu des siens. Rien à configurer.
