---
title: "Admin-Panel"
description: "Das Admin-Panel von Boosting Creator: laufende Aufträge, wartende Spieler, Spielerprofile, Einstellungen und Discord-Logs."
icon: "sliders"
---

Öffne das Panel mit `/boostingcreator` oder `/boostcreator` (siehe [Admin-Berechtigung](/de/boosting-creator/installation#admin-berechtigung)). Jede Änderung gilt sofort, ohne Neustart.

| Tab | Wofür |
| --- | --- |
| **Klassen** | [Klassen](/de/boosting-creator/guides/classes-and-vehicles) und ihre Risiken |
| **Fahrzeuge** | Die Autos jeder Klasse |
| **Orte** | [Jeder Ort](/de/boosting-creator/guides/locations) des Scripts |
| **Fixer** | [Fixer](/de/boosting-creator/guides/fixers) und ihre Wünsche |
| **Live** | Laufende Aufträge und wartende Spieler |
| **Spieler** | Profile, Ruf, Verlauf und Garagen |
| **Einstellungen** | Alles andere |

## Live

Wird alle 5 Sekunden aktualisiert. Für jeden laufenden Auftrag: der Spieler (und die Crew-Mitglieder), der Fixer und der Wunsch, Klasse, Fahrzeug und Kennzeichen, Route, Status mit Badges für Tracker, Verfolgung und Transporter, und die Restzeit. **Abbrechen** beendet einen Auftrag ohne Änderung am Ruf.

**Spieler, die auf ihren nächsten Auftrag warten** listet, wer einen Cooldown hat oder am Tageslimit ist, mit der Restzeit und einem Button **Cooldown aufheben**.

<Frame>
  ![Live-Tab mit einem laufenden Auftrag](/images/boosting-creator/panel-live.jpg)
</Frame>

## Spieler

Jedes Boosting-Profil, Online-Spieler zuerst, durchsuchbar nach Name oder Identifier. Klicke eines an, um es zu öffnen:

- Ruf, Level, erledigte und gescheiterte Aufträge, verdientes Geld
- **Ruf setzen** oder **Ruf geben oder nehmen**
- die Garage mit ihren Autos und ein Button, um ein Auto zu entfernen
- die letzten 25 Aufträge mit Fixer, Wunsch und dem Grund für das Ende
- ein Gefahrenmenü: das Profil zurücksetzen, den Verlauf löschen, die Garage wegnehmen

## Einstellungen

| Kategorie | Was drin ist |
| --- | --- |
| **Allgemein** | Sprache, ACE-Berechtigung, Laptop-Item, Konto für die Bezahlung |
| **Aufträge** | Timing der Angebote, Cooldowns und Tageslimit, Ruf und Bezahlung, VIN-Scratch, Chop Shop, Crews, Fixer und Vertrauen, Garagen, Komplettverkauf und Beschlagnahme, Wachen, Gang-Verfolgung, Polizeirufe beim Aufbrechen |
| **Diebstahl** | Minispiel zum Kurzschließen, Wartezeit bis zum nächsten Versuch und Alarm |
| **Tracker** | Pings, Hacks und Hack-Minispiel |
| **Module** | Siehe [Module](/de/boosting-creator/modules) |
| **Discord** | Logs und Webhooks |

**Standard wiederherstellen** setzt jede Einstellung so zurück, wie sie mit dem Script kam. Klassen, Orte und Fixer bleiben unberührt.

## Discord-Logs

Mit eingeschalteten Discord-Logs loggt das Script das Ende von Aufträgen (mit Fixer und Wunsch), Autos, die zu schnell ankamen, um echt zu sein, abgeschaltete Tracker, VIN-Scratches, gekaufte Garagen, sichergestellte Transporter, abgelehnte Minispiel-Ergebnisse und jede Admin-Änderung. Alles geht an den Haupt-Webhook.

Um einen Log-Typ woandershin zu schicken, füge ihn zu `specificWebhooks` in `current_config.json` hinzu, mit den Typen `contracts`, `vin`, `garages`, `admin` und `cheat`.
