---
title: "Handcuffs-Status setzen"
description: "Setze den Gefesselt-Status eines Spielers direkt, ohne die Fesseln-Animation auszulösen."
icon: "handcuffs"
---

Setzt den Handcuffs-Status eines Spielers, ohne Animation.

<CodeGroup>

```lua Export
exports["jobs_creator"]:setHandcuffs(playerId, state)
```

```lua Beispiel
-- Dies ist nur ein Beispiel und funktioniert so nicht, du musst den Export korrekt verwenden
RegisterNetEvent("hospital_script:playerDead", function(playerId)
    -- Der Script-Code
    -- Der Script-Code
    -- Der Script-Code

    -- Der tote Spieler ist nicht mehr gefesselt
    exports["jobs_creator"]:setHandcuffs(playerId, false)
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Zielspielers |
| `state` | boolean | `true` = gefesselt, `false` = frei |
