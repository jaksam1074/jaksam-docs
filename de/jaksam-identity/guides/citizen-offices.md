---
title: "Bürgerämter"
description: "Starter-Dokumente, Bürgerämter mit einem NPC am Schalter, Gebühren und die esx_dmvschool-Integration."
icon: "building-columns"
---

## Starter-Dokumente

Jeder Charakter, der noch nie ein Dokument der aufgelisteten Typen hatte, bekommt nach dem Laden eines, sobald Name und Geburtsdatum gesetzt sind.

```lua
Config.Starter = {
    documents = { 'id_card' },
    delaySeconds = 15,          -- after the character has loaded
}
```

Starter-Dokumente haben **kein Foto**: Das Foto wird bei einer Verlängerung im Amt aufgenommen. Setze `documents = {}`, um das abzuschalten.

## Bürgerämter

Ein Amt ist ein NPC an einem Schalter, mit einem Blip auf der Karte. Jedes Amt bearbeitet die Dokumenttypen, die es auflistet. Spieler können:

- ein erstes Dokument **beantragen**
- es **verlängern**: gleiche Nummer, neues Ablaufdatum und Foto (das Dokument muss mitgeführt werden)
- **Ersatz** bekommen, wenn es verloren oder gestohlen wurde: neue Nummer, die alte wird ungültig
- ein Dokument als verloren oder gestohlen **melden**, oder es als **wiedergefunden melden**
- eigene Karten, die nicht mehr gültig sind, **abgeben**
- eine **Klasse hinzufügen**, die nach dem Druck der Karte erworben wurde (läuft als Verlängerung)

Das Foto wird am Schalter aufgenommen. Ein gesperrtes, entzogenes oder eingezogenes Dokument blockiert den Schalter für diesen Typ. **Dienstausweise werden hier nie ausgestellt**, das macht der Boss des Jobs.

<Note>
  Eine Karte, die nicht dem Spieler gehört, bekommt dieselbe Antwort, egal ob sie jemand anderem gehört oder gefälscht ist. Das Amt kann also nicht zum Testen von Fälschungen benutzt werden.
</Note>

### Konfiguration

Ämter werden in `Config.Offices` (`config/office.lua`) eingerichtet, oder im Spiel auf der Ämter-Seite von `/documents config` platziert.

```lua
Config.Offices = {
    payAccount = 'money',       -- 'money' (cash) | 'bank'
    pedDistance = 40.0,         -- a counter NPC exists only while the player is this close (metres)
    fees = {                    -- per document type; 0 = free
        id_card = { first = 100, renew = 50, replace = 150 },
        drive = { first = 250, renew = 100, replace = 300 },
        weapon = { first = 1000, renew = 400, replace = 1200 },
    },
    locations = {
        { label = L('office_city_hall'), coords = vec4(-517.63, -251.57, 35.67, 207.0), model = 'a_f_y_business_01',
          documents = { 'id_card', 'drive' }, blip = { sprite = 498, color = 0, scale = 0.7 } },
    },
}
```

Gebühren werden erst bezahlt, wenn Foto und Ausstellung geklappt haben.

<Tip>
  Du kannst ein Amt pro Behörde eröffnen, zum Beispiel einen DMV-Schalter, der nur `drive` bearbeitet, und einen Polizeischalter, der nur `weapon` bearbeitet.
</Tip>

## esx_dmvschool (nur ESX)

esx_dmvschool gibt nach einer bestandenen Prüfung die Lizenz, aber keine Karte. Mit `Config.DmvSchool`:

- wird der **erste Führerschein direkt nach der Prüfung ausgestellt**, mit einem dort aufgenommenen Foto und ohne Gebühr (die Schule hat schon kassiert)
- wird eine später bestandene Klasse **auf den Führerschein gedruckt, den der Spieler trägt** (gleiche Nummer, Ablaufdatum und Foto)
- wird der Spieler ohne Karte dabei ins Amt geschickt, das sie hinzufügt

```lua
Config.DmvSchool = {
    enabled = true,
    document = 'drive',         -- the document type its licences are classes of
}
```

<Warning>
  Das Event `esx_dmvschool:addLicense` wird von esx_dmvschool auf dem Server nicht geprüft, ein cheatender Client kann sich damit also jede Lizenz geben. Sichere das Event in esx_dmvschool ab, oder setze `Config.DmvSchool.enabled = false`, auf einem Live-Server.
</Warning>

## Rathaus bei QBCore und Qbox

In der QBCore-Version wird, was qb-core, qbx_core und qb-cityhall / qbx_cityhall ausgeben, zu einem registrierten Dokument des Charakters. qbx_cityhall stellt es mit einem dort aufgenommenen Foto aus. Entferne auf Qbox `qbx_idcard`: Jaksam Identity antwortet an seiner Stelle.
