---
title: "Fälscherwerkstätten"
description: "Fälscherwerkstätten hinzufügen, Jobs sie kaufen und verkaufen lassen, und Upgrades, Lager und Zutritt einstellen."
icon: "warehouse"
---

Eine Werkstatt ist eine Tür irgendwo in der Welt, die in eine eigene Kopie des Fälscherraums führt (der Biker-Fake-ID-Innenraum aus `bob74_ipl`). Sie gehört einem Job oder niemandem.

<Warning>
  **Ab Werk ist keine Werkstatt eingerichtet.** Die ganze Fälscherseite bleibt unsichtbar, bis du eine in `config/forgery.lua` oder im Spiel mit `/documents config` hinzufügst.
</Warning>

## Eine Werkstatt hinzufügen

In `Config.Forgery.workshops` (`config/forgery.lua`):

```lua
workshops = {
    docks = { label = 'Docks', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 150000, jobs = {}, minGrade = 0 },
    east_side = { label = 'East side', entrance = vec4(0.0, 0.0, 0.0, 0.0), price = 90000, jobs = { 'vagos', 'ballas' }, minGrade = 1 },
},
```

| Feld | Beschreibung |
| --- | --- |
| `label` | Name der Werkstatt |
| `entrance` | Die Tür draußen, ein `vec4` mit der Blickrichtung nach draußen |
| `price` | Was ein Job für den Kauf zahlt |
| `jobs` | Die Jobs, die sie besitzen dürfen, `{}` für alle Jobs |
| `minGrade` | Niedrigster Rang des besitzenden Jobs, der hinein darf |
| `owner` | Optional: der Job, dem sie ab dem ersten Start gehört |

<Tip>
  Im Spiel geht es einfacher: Drücke auf der Werkstatt-Seite von `/documents config` **Place**, geh zur Tür und klicke. Admins fügen dort auch Werkstätten hinzu und entfernen sie, während der Server läuft, und geben eine Werkstatt einem Job oder nehmen sie weg.
</Tip>

## Kaufen und besitzen

- **Kaufen:** Eine Werkstatt ohne Besitzer zeigt an ihrer Tür "Workshop for sale". Der Boss eines Jobs kauft sie für den Job mit Schwarzgeld (`Config.Forgery.payAccount`).
- **Mehrere pro Job:** Ein Job kann so viele besitzen, wie er bezahlen kann, oder so viele, wie `ownership.perJob` erlaubt.
- **Wer der Boss ist:** der höchste Rang des besitzenden Jobs, und so viele Ränge darunter, wie `ownership.bossDepth` angibt. Der Boss kauft, verkauft, stellt ein und rüstet auf.
- **Mitglieder** des besitzenden Jobs kommen ab dem `minGrade` der Werkstatt hinein. Andere klingeln, und ein Mitglied drinnen kann sie hereinlassen.
- **Verkaufen:** Der Boss verkauft sie am Werkstatt-Laptop (Seite Upgrades) und bekommt `ownership.refund` des gezahlten Preises zurück (nichts für eine Werkstatt, die ein Admin vergeben hat). `ownership.sellable = false` schaltet das ab.

```lua
ownership = {
    perJob = 0,           -- workshops one job may own (0 = as many as it can pay)
    bossDepth = 0,        -- ranks below a job's highest that may buy, sell and manage too
    sellable = true,      -- the boss may sell the workshop at its laptop
    refund = 0.5,         -- share of what was paid that comes back when it is sold
    onRelease = 'room',   -- what stays when a workshop loses its owner
},
```

### Was bleibt, wenn eine Werkstatt ihren Besitzer verliert

| `onRelease` | Ergebnis |
| --- | --- |
| `room` | Upgrades und Lager bleiben, Arbeiter werden entlassen und offene Aufträge verworfen |
| `all` | Alles bleibt für den nächsten Besitzer |
| `nothing` | Ein leerer Raum |

<Info>
  **Schwarzgeld:** Auf ESX das Konto `black_money`, auf QBCore das Item `markedbills` (Wert in `metadata.worth`), auf Qbox das stapelbare Item `black_money`.
</Info>

## Upgrades

Der Boss kauft Upgrades am Laptop, mit Schwarzgeld.

| Upgrade | Was es ändert |
| --- | --- |
| **Ausrüstung** | Die höchste Qualität, die eine hier gemachte Fälschung erreichen kann (keine, Basis bis 70, Profi bis 100), wie viele Arbeiter Platz haben, und die Prägemaschine (nur Profi) |
| **Sicherheit** | Wie lange Beamte brauchen, um die Tür aufzubrechen (30 Sekunden, 90 mit dem Upgrade), und ein Alarm an Mitglieder woanders während einer Razzia |
| **Stil** | Das Aussehen des Innenraums |

Die Preise stehen in `Config.Forgery.upgrades`, oder im Spiel.

## Der Boss-Laptop

Der Laptop auf dem Boss-Schreibtisch zeigt seine Seite auf dem echten Bildschirm im Raum, mit Tabs:

- **Übersicht:** Arbeiter, Geräte und Tische
- **Personal:** Arbeiter und Wache einstellen und entlassen, Löhne zahlen, festlegen, was die Arbeiter bei einer Razzia vernichten
- **Tickets:** die Auftragswarteschlange
- **Material:** Material bestellen, nach einer Wartezeit ins Rohstofflager geliefert
- **Upgrades:** Upgrades kaufen, die Werkstatt verkaufen

## Lager

Jede Werkstatt hat drei Lager, die sich an ihren Regalen öffnen:

| Lager | Inhalt |
| --- | --- |
| Rohstoffe | Rohlinge, Toner und alles, was das Fälschen braucht |
| Frei | Frei für die Spieler |
| Ergebnisse | Wo die Arbeiter die fertigen Dokumente ablegen |

Die Größen stehen in `Config.Forging.stores`. Arbeiter legen die Dokumente eines Auftrags in einen **ID-Stapel** (`id_stack`), einen Container, der sie in einem Slot hält. Ein Dokument auf ein anderes zu ziehen, macht ebenfalls einen Stapel. qb-inventory hat keine Container, dort kommen die Dokumente einzeln an.

<Note>
  Jedes Target reicht 2 Meter (`Config.TargetDistance`), und der Server nimmt Aktionen nur von einem Mitglied an, das an der Station steht. Gäste und Beamte drinnen sehen keine der Stationen.
</Note>
