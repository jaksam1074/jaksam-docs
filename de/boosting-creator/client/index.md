---
title: "Client"
description: "Client-seitige Exports von Boosting Creator: die Hilfe-Benachrichtigung ersetzen, den Skill Check aus deinen eigenen Scripts nutzen."
icon: "laptop"
---

## Die Hilfe-Benachrichtigung ersetzen

Die Texte `Press E to ...` nutzen die native Hilfe-Benachrichtigung oder das **Text-UI**-[Modul](/de/boosting-creator/modules), das du in den Einstellungen wählst. Um sie selbst zu zeichnen:

```lua
exports["boosting_creator"]:replaceShowHelpNotification(function(message)
    -- show message with your own UI
end)
```

Die Funktion wird jeden Frame aufgerufen, solange der Text auf dem Bildschirm sein soll.

## Skill Check

Die Skill-Check-Leiste des Scripts kann von anderen Scripts genutzt werden.

```lua
local success = exports["boosting_creator"]:skillcheck(difficulty)
```

| Parameter | Typ | Beschreibung |
| --- | --- | --- |
| `difficulty` | `number` | 1 bis 3 |
| `speed` | `number` (optional) | Geschwindigkeit der beweglichen Markierung, überschreibt die Schwierigkeit |
| `positiveBars` | `number` (optional) | Größe der zu treffenden Zone, überschreibt die Schwierigkeit |

Gibt `true` bei Erfolg zurück, `false` bei Misserfolg oder wenn schon ein anderer Skill Check offen ist. Es wartet, bis der Spieler fertig ist.

Um einen offenen Skill Check zu schließen (er gibt `false` zurück):

```lua
exports["boosting_creator"]:cancelSkillcheck()
```

## Benachrichtigungen, Fortschrittsbalken und Dispatch

Sie werden mit [Modulen](/de/boosting-creator/modules) ersetzt, nicht mit Exports.

## Eigene Minispiele

Siehe [Eigenes Minispiel einbauen](/de/boosting-creator/guides/minigames#eigenes-minispiel-einbauen).
