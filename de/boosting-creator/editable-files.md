---
title: "Editierbare Dateien"
description: "Die Dateien von Boosting Creator, die zum Bearbeiten gedacht sind: Kennzeichenformat, Polizei-Jobs, Debug, externe Event-Namen, QBCore-Garage und die Hooks."
icon: "file-pen"
---

Der Großteil von Boosting Creator wird im Spiel eingerichtet. Einige Dinge liegen stattdessen im Ordner `integrations/`, weil sie Code sind oder sich selten ändern.

<Warning>
  Behalte eine Kopie dieser Dateien, bevor du das Script aktualisierst: Ein Update kann sie ersetzen.
</Warning>

## integrations/sh_integrations.lua

| Wert | Was er macht |
| --- | --- |
| `EXAMPLE_PLATE` | Format der Auftragskennzeichen. Buchstaben und Zahlen sind zufällig, `#` markiert den festen Teil: `"#BST#123"` ergibt `BST920`, `BST945`... Höchstens 8 Zeichen. |
| `POLICE_JOBS_NAMES` | Jobs, die als [Polizei](/de/boosting-creator/guides/police) zählen. |
| `SECONDS_TO_REFRESH_SHARED_OBJECT` | Das Framework-Objekt alle X Sekunden aktualisieren, `nil` für nie. |
| `DEBUG_OUTPUTS` | Debug-Zeilen in der Server-Konsole und in F8. Alternativ `setr boosting_creator_debug 1` in der `server.cfg`, ohne die Datei zu bearbeiten. Schalte es ein, wenn du den Support um Hilfe bittest. |

## integrations/sv_integrations.lua

| Wert | Was er macht |
| --- | --- |
| `EXTERNAL_EVENTS_NAMES` | Nur ändern, wenn dein Framework seine Events umbenannt hat und das Script sie nicht findet. |
| `VIN_SCRATCH_QB_GARAGE` | Nur QBCore: die Garage, in der ein Auto mit abgeschliffener VIN gespeichert wird, standardmäßig `pillboxgarage`. |
| `CanPlayerJoinBoostingQueue` | [Hook](/de/boosting-creator/server#canplayerjoinboostingqueue), um einen Spieler aus der Warteschlange herauszuhalten. |
| `OnBoostingContractEnded` | [Hook](/de/boosting-creator/server#onboostingcontractended), der aufgerufen wird, wenn ein Auftrag endet. |

## integrations/cl_integrations.lua

| Wert | Was er macht |
| --- | --- |
| `DEFAULT_PROGRESSBAR_COLOR` | Farbe des Standard-Fortschrittsbalkens, als Hex-Code. |
| `BLIP_TIME_AFTER_POLICE_ALERT` | Sekunden, die der Alarm-Blip des Dispatch-Moduls `default` auf der Karte bleibt, standardmäßig 120. |
| `EXTERNAL_SCRIPTS_NAMES` | Ordnernamen von `datacrack`, `utk_fingerprint` und `ultra-keypackhack`, falls du sie umbenannt hast. |

## current_config.json

Die Einstellungen des Panels werden in `boosting_creator/current_config.json` gespeichert. Bearbeite sie im Panel. Zwei Werte haben dort kein Feld:

- `specificWebhooks`: ein Discord-Webhook pro Log-Typ, siehe [Discord-Logs](/de/boosting-creator/guides/admin-panel#discord-logs)
- `minigamesMinSeconds`: die kürzeste Zeit, die ein Minispiel dauern darf, siehe [Minispiele](/de/boosting-creator/guides/minigames#eigenes-minispiel-einbauen)

Stoppe das Script, bevor du die Datei von Hand bearbeitest, sonst kann das Panel deine Änderung überschreiben.
