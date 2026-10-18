---
title: "Fälschen, Arbeiter und Aufträge"
description: "Wie Spieler Dokumente von Hand fälschen, wie die Qualität entsteht, und wie NPC-Arbeiter und die Auftragswarteschlange funktionieren."
icon: "print"
---

## Fälschen von Hand

Eine Fälschung durchläuft die Stationen der Werkstatt, ein Ticket nach dem anderen:

<Steps>
  <Step title="Foto">
    Am Hintergrund: fotografiere dich selbst oder einen anderen Spieler, oder ruf einen NPC-Arbeiter mit Kamera herbei. Profi-Ausrüstung gibt einen transparenten Fotohintergrund.
  </Step>
  <Step title="Dateneingabe">
    An einem Computer oder Laptop: Name, Geburtsdatum und die anderen gedruckten Daten eingeben.
  </Step>
  <Step title="Drucken">
    Verbraucht einen Rohling und Toner aus dem Drucker.
  </Step>
  <Step title="Laminieren">
    An einem Laminiertisch.
  </Step>
  <Step title="Prägen (optional)">
    Nur mit Profi-Ausrüstung, bringt Qualität.
  </Step>
  <Step title="Schneiden">
    Am Papierschneider: Das Dokument ist fertig.
  </Step>
</Steps>

Jede Station hat einen **Skill-Check**: Ein Erfolg bringt Qualität, ein Fehlschlag kostet welche (`Config.Forging.check`, und `Config.Forging.emboss` für die Prägemaschine). Du kannst das Minispiel ersetzen, siehe [Skill-Check](/de/jaksam-identity/client/skill-check).

### Kopien

Ein Spieler kann ein Dokument kopieren, das er trägt. Daten und Foto kommen vom Original, und die Felder lassen sich ändern: eine echte Vorlage mit falschem Namen. Die Kopie einer Fälschung ist auf die Qualität des Originals minus `Config.Forging.copyLoss` begrenzt.

### Qualität

Die Qualität einer Fälschung (5 bis 100) ergibt sich aus:

- dem **Level des Fälschers**: Jede Fälschung bringt Erfahrung, und das Level bestimmt die Grundqualität und was gefälscht werden kann (erst Ausweise, dann Lizenzen, dann Dienstausweise)
- den Skill-Checks an den Stationen
- ein wenig Glück

Danach wird sie durch die **Ausrüstung** der Werkstatt und den verwendeten **Rohling** begrenzt (`doc_blank` bis 60, `doc_blank_secure` bis 100).

```lua
levels = {
    { xp = 0,    base = 35, kinds = { identity = true } },
    { xp = 150,  base = 45, kinds = { identity = true, license = true } },
    { xp = 500,  base = 58, kinds = { identity = true, license = true } },
    { xp = 1200, base = 70, kinds = { identity = true, license = true, badge = true } },
    { xp = 2500, base = 82, kinds = { identity = true, license = true, badge = true } },
},
```

Die Qualität entscheidet, welche Fehler auf einen Blick, in der Hand, unter UV oder erst im Register auffallen. Siehe [Falsche Dokumente und Fehler](/de/jaksam-identity/guides/documents-and-register#falsche-dokumente-und-fehler).

### Material

| Item | Verwendung |
| --- | --- |
| `doc_blank` | Kartenrohling, Qualität bis 60 |
| `doc_blank_secure` | Sicherheitsrohling, Qualität bis 100 |
| `printer_toner` | Tonerkartusche, je `Config.Forging.tonerCharges` Drucke |
| `pvc_sheet` | Arbeiter machen daraus Kartenrohlinge |
| `holo_foil` | Arbeiter machen daraus mit einem Rohling einen Sicherheitsrohling |

Material wird an einem Laptop mit Schwarzgeld bestellt und nach einer Wartezeit ins Rohstofflager geliefert (`Config.Forging.orders`).

## Aufträge

Ein Auftrag ist eine Anzahl Tickets eines Dokumenttyps und Rohlings, aus denen sich Arbeiter und Spieler bedienen (dringende zuerst, dann die ältesten).

- **Priorität:** niedrig, normal oder dringend
- **Zuständig:** alle, ein Spieler oder ein Arbeiter
- **Pausieren, fortsetzen, abbrechen**
- **Feste Daten:** Ein Auftrag aus einer Kopie oder einem Datensatz wiederholt ihn auf seinen Tickets
- **Serien:** erfundene Identitäten ohne Foto, direkt an die Arbeiter übergeben
- **Übergeben:** Ein Ticket kann den Arbeitern oder einem Arbeiter übergeben und zurückgeholt werden

Jede Aktion braucht einen Mindestrang im Job:

```lua
queue = {
    maxAmount = 50,            -- tickets per order
    maxOpenTickets = 300,      -- open tickets per workshop
    offlineMinutes = 10,       -- an order assigned to a player who stays away this long goes back to everyone
    rights = { create = 0, priority = 1, assign = 2, pause = 1, cancel = 2, handover = 0 },
},
```

## NPC-Arbeiter

Der Boss stellt Arbeiter am Laptop ein. Sie gehen von Gerät zu Gerät, bringen Tickets durch Drucker, Laminiertisch und Schneider, füllen die Drucker mit Toner auf und tragen die fertigen Dokumente ins Ergebnislager.

| Stufe | Grundqualität | Tempo | Fehlerquote | Tickets gleichzeitig |
| --- | --- | --- | --- | --- |
| Anfänger | 40 | 1.0 | 35% | 1 |
| Erfahren | 60 | 1.3 | 20% | 3 |
| Profi | 78 | 1.6 | 10% | 5 |

- **Rollen:** fälschen, oder Material herstellen (PVC zu Rohlingen, Rohling und Folie zu Sicherheitsrohlingen)
- **Arbeiterkarten:** Bei einem Arbeiter siehst du die Stufe, einen Live-Status mit Timer und Balken für Tempo, Fehlerquote, Bogengröße und Kartuschen. Gib direkt Aufgaben: Toner holen, einen Auftrag oder ein Ticket übernehmen, Rolle wechseln, entlassen
- **Löhne:** Der Boss zahlt Schwarzgeld ein, und die Löhne werden einmal pro Zeitraum abgezogen. Ein unbezahlter Arbeiter kündigt. Versiegelte Zeit nach einer Razzia kostet nichts
- **Wache:** Eine Sicherheitswache pro Werkstatt warnt alle drinnen, wenn Beamte die Tür aufbrechen
- Die Qualität eines Arbeiters übersteigt nie die Grundqualität des besten Spieler-Fälschers des besitzenden Jobs
- Die Zahl der Arbeiter hängt vom Ausrüstungs-Upgrade ab

Einstellpreise, Löhne und Arbeitszeiten stehen in `config/npc.lua`, oder im Spiel auf der Arbeiter-Seite von `/documents config`.

<Tip>
  `Config.Bridge.menu = 'ox_lib'` ersetzt die Interaktionskarten an Arbeitern und Stationen durch ox_lib-Kontextmenüs.
</Tip>

## Demo-Modus

Für Showcase-Videos und Demo-Server: Die Lager sind immer gefüllt, die Arbeitszeiten kurz, nichts kostet Geld und niemand scheitert. Schalte ihn mit `Config.Demo = true` oder `/documents demo on` ein (wird nach einem Neustart nicht behalten).
