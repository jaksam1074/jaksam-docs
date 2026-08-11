---
title: "Prüfen, ob ein Spieler im Dienst ist"
description: "Prüfe, ob ein bestimmter Spieler aktuell im Dienst ist."
icon: "briefcase"
---

Gibt zurück, ob der Spieler im Dienst ist oder nicht.

<CodeGroup>

```lua Export
exports["jobs_creator"]:isPlayerOnDuty(playerId)
```

```lua Beispiel
local playerId = 52
print("Spieler-ID " .. playerId .. " ist im Dienst: " .. tostring(exports["jobs_creator"]:isPlayerOnDuty(playerId)))
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Zielspielers |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `isOnDuty` | boolean | **true**, wenn der Spieler im Dienst ist, **false**, wenn der Spieler nicht im Dienst ist |
