---
title: "Befehle"
description: "Vollständige Liste der /documents-Admin-Befehle und der Spielerbefehle von Jaksam Identity."
icon: "slash-forward"
---

## Wer sie benutzen kann

`/documents <unterbefehl>` funktioniert in der Server-Konsole, für Spieler mit der ACE `jksm_identity.admin` und für die Framework-Gruppen in `Config.AdminGroups`. Ohne Unterbefehl listet es alle auf.

```cfg
add_ace group.admin jksm_identity.admin allow
```

Der Befehlsname ist `Config.AdminCommand` (Standard `documents`).

## Admin-Befehle

| Unterbefehl | Was |
| --- | --- |
| `config` | Öffnet die [Einstellungen im Spiel](/de/jaksam-identity/guides/settings-in-game) |
| `issue <playerId> <type> [nophoto] [force] [grant] [grant:<licence type>]` | Ein echtes Dokument ausstellen |
| `check <serial>` | Registerabfrage, wie eine Behörde sie sieht |
| `truth <serial>` | Admin-Ansicht: echt, gefälscht (mit Qualität und Hersteller) oder unbekannt |
| `license <playerId> list \| add <type> \| remove <type>` | Lizenzen eines Charakters |
| `forge <playerId> <type> <quality 0-100> [nophoto] [copy:<serial>]` | Eine Fälschung geben |
| `workshop <job> \| leave` | Eine Werkstatt betreten oder verlassen |
| `exit <playerId> \| all` | Spieler aus den Werkstätten schicken |
| `toner <job> <prints>` | Den Druckertoner einer Werkstatt setzen |
| `raid [<workshop> [end \| unseal \| reset]]` | Razzien und Siegel auflisten, eine Razzia beenden, ein Siegel aufheben, die Wartezeit bis zur nächsten Razzia löschen |
| `order <job> <type> <amount> [low\|normal\|urgent] [assignee]` | Einen Auftrag erstellen |
| `orders <job>` | Die Aufträge einer Werkstatt auflisten |
| `ordercmd <job> <id> <action> [value]` | Einen Auftrag verwalten |
| `demo on \| off \| refill` | Demo-Modus für Showcases (`Config.Demo`) |

### Optionen von issue

| Option | Wirkung |
| --- | --- |
| `nophoto` | Ohne Foto ausstellen |
| `force` | Auch ausstellen, wenn Lizenz oder Job fehlen |
| `grant` | Dem Charakter zusätzlich jede Lizenz des Dokuments geben |
| `grant:<licence type>` | Dem Charakter zusätzlich eine Lizenz geben, zum Beispiel `grant:drive_truck` |

```bash
/documents issue 12 id_card            # ID card with photo for player 12
/documents issue 12 drive grant        # driver licence, granting the licence first
/documents check SAAB1234567           # what the police would see
/documents forge 12 drive 80           # a forged driver licence of quality 80
```

<Note>
  Mit `Config.Debug = true` gibt es zusätzlich Messbefehle (`/jksm_pos`, `/jksm_aim`, ...) und Test-Unterbefehle, nur für Admins. Schalte `Config.Debug` auf einem Live-Server ab: Dann existieren sie nicht.
</Note>

## Spielerbefehle

| Befehl | Was |
| --- | --- |
| `/businesscards` | Visitenkarten für deinen Job drucken, siehe [Visitenkarten](/de/jaksam-identity/guides/business-cards) |
