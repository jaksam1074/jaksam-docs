---
title: "Dokument zeigen"
description: "Einem Spieler in der Nähe ein Dokument, das der Spieler trägt, als 3D-Karte zeigen."
icon: "eye"
---

Zeigt einem anderen Spieler ein mitgeführtes Dokument als 3D-Karte, genau als würde es aus dem Inventar gezeigt. Der Spieler muss das Dokument tragen, und beide Spieler müssen in derselben Instanz und innerhalb von `Config.ShowDistance` sein.

<CodeGroup>

```lua Export
exports["jksm_identity"]:ShowDocument(playerId, targetId, serial)
```

```lua Example
RegisterNetEvent("my_phone:showCard", function(targetId, serial)
    local ok, reason = exports["jksm_identity"]:ShowDocument(source, targetId, serial)
    if not ok then
        TriggerClientEvent("my_phone:notify", source, "Could not show the card: " .. reason)
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers, der das Dokument zeigt |
| `targetId` | integer | Server-ID des Spielers, der es sieht |
| `serial` | string | Die Nummer eines Dokuments, das der Spieler trägt |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `ok` | boolean | **true**, wenn die Karte gezeigt wurde |
| `reason` | string \| nil | `bad_target` (ungültig oder derselbe Spieler), `too_far` (andere Instanz oder zu weit weg), `no_card` (der Spieler trägt dieses Dokument nicht) |
