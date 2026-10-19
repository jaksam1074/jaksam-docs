---
title: "Dokumente und Register"
description: "Wie Dokumente, Lizenzklassen, das Register und gefälschte Karten in Jaksam Identity funktionieren, und wie du eigene Dokumenttypen hinzufügst."
icon: "id-card"
---

## So funktioniert es

<CardGroup cols={2}>
  <Card title="Das Dokument ist die Identität" icon="id-card">
    Eine Abfrage liefert die Identität, die auf dem Dokument gedruckt ist. Das Script prüft nie, wer es trägt: Ein gestohlenes echtes Dokument funktioniert, bis sein Besitzer es meldet.
  </Card>

  <Card title="Nur der Server weiß, was echt ist" icon="server">
    Echte Nummern liegen im Register (`jksm_identity_documents`), gefälschte in `jksm_identity_forgeries` mit ihrer Qualität. Ein echtes und ein gefälschtes Item tragen genau dieselben Metadaten.
  </Card>

  <Card title="Fakten, kein Zwang" icon="scale-balanced">
    Ablauf, Sperren und alte Fotos werden auf der Karte und in der Registerabfrage angezeigt. Nichts wird automatisch entfernt, blockiert oder verlängert: Was folgt, ist Roleplay.
  </Card>

  <Card title="Das Framework hält die Lizenzen" icon="list-check">
    ESX: die esx_license-Tabellen (`licenses`, `user_licenses`). QBCore/Qbox: die Charakter-Metadaten `licences`.
  </Card>
</CardGroup>

<Note>
  **Anonymität:** Das Foto wird von einem lokalen, nicht vernetzten Klon des Charakters aufgenommen, ohne Maske, Hut und Brille. Niemand in der Nähe sieht das Gesicht, und das Foto zeigt keine Maske.
</Note>

## Dokumenttypen

Dokumenttypen werden in `Config.Documents` (`config/documents.lua`) eingerichtet. Es gibt drei Arten:

| Art | Im Register gültig, wenn | Beispiel |
| --- | --- | --- |
| `identity` | der Status des Eintrags gültig ist | Personalausweis |
| `license` | der Status gültig ist **und** die Lizenz (oder mindestens eine ihrer Klassen) noch vorhanden ist | Führerschein (Klassen A, B, C), Waffenschein |
| `badge` | der Status gültig ist **und** der Besitzer den Job noch hat | LSPD, LSMD, LSC |

Jeder Eintrag hat diese Felder:

| Feld | Beschreibung |
| --- | --- |
| `item` | Der Name des Inventar-Items (das Item muss in deinem Inventar existieren) |
| `kind` | `identity`, `license` oder `badge` |
| `license` | (nur `license`) der Lizenztyp: ESX die Tabelle `licenses`, QBCore/Qbox der Schlüssel in den Metadaten `licences` |
| `licenses` | (nur `license`, statt `license`) ein Dokument für mehrere Lizenztypen, jeder eine Klasse |
| `job` | (nur `badge`) der Job, zu dem der Ausweis gehört |
| `validityDays` | Tage bis zum Ablauf, `nil` für nie |
| `layout` | `id` (Querformat, Standard) oder `badge` (Dienstausweis im Hochformat) |
| `theme` | Aussehen der Karte: Kopfzeile, Titel, Farben. Dienstausweise haben zusätzlich `word`, `emblem` (`star`, `shield`, `starOfLife`, `wrench`), `authority` und `authorityName` |

### Lizenzklassen

Ein Dokument kann mehrere Lizenztypen als Klassen abdecken:

```lua
drive = {
    item = 'driver_license',
    kind = 'license',
    licenses = { drive_bike = 'A', drive = 'B', drive_truck = 'C' },
    label = L('doc_driver'),
    validityDays = 180,
},
```

Die Karte druckt die Klassen, die bei der Ausstellung vorhanden waren. Die Registerabfrage zeigt die Klassen von jetzt und nennt jede gedruckte Klasse, die entzogen wurde.

### Eigenes Dokument anlegen

Jede Lizenz deines Frameworks kann ein Dokument werden. Füge das Item zu deinem Inventar hinzu, dann einen Eintrag hier:

```lua
hunting = { item = 'hunting_license', kind = 'license', license = 'hunting', label = 'Hunting licence', validityDays = 120 },
```

Die vollständige Anleitung, mit dem Item für jedes Inventar, dem Aussehen der Karte, den Ämtern und den Dienstausweisen, steht in [Eigenes Dokument erstellen](/de/jaksam-identity/guides/custom-documents).

### Item-Metadaten

Jedes Dokument trägt dieselben Felder: `serial`, `firstname`, `lastname`, `dob`, `sex`, `issued`, `expires`, `photo`, und `classes` bei Lizenzklassen. `photo` ist nur eine Foto-ID: Das Bild liegt in der Tabelle `jksm_identity_photos`.

## Register-Status

Jedes echte Dokument hat einen Status im Register:

| Status | Bedeutung |
| --- | --- |
| `valid` | Alles in Ordnung |
| `lost` / `stolen` | Vom Besitzer in einem Bürgeramt gemeldet |
| `seized` | Von einer Behörde eingezogen |
| `suspended` | Bis zu einem festgelegten Zeitpunkt gesperrt, danach wieder gültig |
| `replaced` | Dem Besitzer wurde ein neueres Dokument desselben Typs ausgestellt |
| `revoked` | Endgültig entzogen |

Ein neues Dokument ersetzt immer das alte: Das ältere gültige Dokument dieses Typs wird als `replaced` markiert.

## Die Registerabfrage

Die Registerabfrage ist das, was eine Behörde sieht. Sie meldet:

- **Kein Eintrag:** Die Nummer ist unbekannt, und ob eine Person mit dem gedruckten Namen überhaupt existiert
- **Status:** verloren, gestohlen, eingezogen, gesperrt, ersetzt oder entzogen
- **Abgelaufen:** Das Ablaufdatum ist überschritten
- **Lizenz fehlt / Klasse entzogen:** Die Lizenz oder eine der gedruckten Klassen ist nicht mehr vorhanden
- **Job verlassen:** Der Besitzer des Dienstausweises hat diesen Job nicht mehr
- **Abweichende Daten:** Der gedruckte Name oder das Geburtsdatum weicht vom Register ab

Sie verrät nie, wer eine Fälschung gemacht hat oder ihre Qualität. Admins sehen das mit `/documents truth <serial>`.

## Ein Dokument benutzen und zeigen

`Config.UseAction` entscheidet, was das Benutzen eines Dokument-Items macht:

| Wert | Verhalten |
| --- | --- |
| `auto` | Zeigt es dem nächsten Spieler innerhalb von `Config.ShowDistance`, sieht es an, wenn niemand da ist |
| `view` | Sieht es immer an |
| `show` | Zeigt es immer |
| `menu` | Fragt jedes Mal |

Dokumente werden nur Spielern in derselben Instanz gezeigt. **Aus der Entfernung sind nur grobe Fehler sichtbar**, in der Hand bekommst du den genauen Blick.

## Falsche Dokumente und Fehler

Eine gefälschte Karte zeigt Fehler auf drei Ebenen. Wie viele, hängt von ihrer Qualität ab:

| Ebene | Beispiele |
| --- | --- |
| Auf einen Blick | Siegel verschoben, falsche Schrift, Farbe daneben |
| In der Hand | Unscharfes Foto, verrutschter Text, fehlende Mikroschrift, flaches Hologramm |
| Unter UV | UV-Merkmal fehlt |

Die UV-Ebene erscheint, solange der Betrachter das UV-Lampen-Item trägt (`Config.UvItem`, Standard `uv_lamp`). Eine gute Fälschung kann jede Sichtprüfung bestehen und erst im Register auffallen.

<Info>
  Ein Dokument aus einem jaksam-Shop oder einer Admin-Vergabe ist **registriert** (echt), außer seine jaksam-`rarity` steht in `Config.UnregisteredRarities`. Dann wird es eine nicht registrierte Fälschung mit der Qualität `Config.UnregisteredQuality`.
</Info>
