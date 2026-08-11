---
title: "Metadata"
icon: "tags"
description: "Item-Metadaten für Spieler anzeigen und Standard- oder dynamische Metadatenwerte festlegen"
---

## Wie man Spielern Metadaten anzeigt

Spielern bestimmte Metadaten anzuzeigen ist einfach. Zuerst musst du wissen, wie der Metadaten-Key heißt, den du anzeigen willst. Dazu kannst du im `/inventory`-Einstellungsmenü den "Debug-Modus" aktivieren und dann mit der Maus über das gewünschte Item fahren.

<Columns cols={2}>
  <Frame>
    ![Item debug settings screenshot](/images/metadata-debug-settings.png)
  </Frame>

  <Frame>
    ![Item debug metadata screenshot](/images/metadata-debug-item.png)
  </Frame>
</Columns>

### Für ein einzelnes Item hinzufügen

Um Spielern die Metadaten eines einzelnen Items anzuzeigen, kannst du diesen Code in der jeweiligen Item-Definition anpassen, in der Datei `jaksam_inventory/_data/items.lua`:

```lua
displayFields = {
    { field = 'YOUR_METADATA_KEY_HERE', label = 'TEXT YOU WANT HERE: ${value}'}, -- Zufälliges Beispiel
    { field = 'ammo', label = 'Ammo: ${value}'}, -- Nützlich bei Waffen (standardmäßig schon eingebaut)
    { field = 'plate', label = 'Plate: ${value}'}, -- Nützlich bei Fahrzeugschlüsseln
},
```

<Frame>
  ![Single item display fields example](/images/metadata-single-item-example.png)
</Frame>

### Für alle Item-Typen hinzufügen

Um Spielern die Metadaten eines ganzen Item-Typs anzuzeigen, ist die Methode zu 100 % identisch, nur dass du es in der `Script.defaultsByType`-Tabelle einträgst, in der Datei `jaksam_inventory/_data/defaults.lua`.

### Optional: Metadatenwerte schöner darstellen

Manchmal willst du Metadaten Spielern in einer schöneren Form zeigen. Zum Beispiel, statt "weapon_pistol" anzuzeigen, willst du "Pistol" zeigen. Hier kommen Formatter ins Spiel!

<Tip>
  Ein Formatter ist wie ein Übersetzer: er nimmt den Originalwert (z.B. `weapon_pistol`) und wandelt ihn in etwas Schöneres um (z.B. `Pistol`).
</Tip>

Du kannst eingebaute Formatter nutzen oder eigene in `jaksam_inventory/_data/formatter.lua` erstellen. So werden sie genutzt:

```lua
displayFields = {
    { field = 'item', label = 'Label: ${value}', formatterId = "itemNameToLabel"}, -- Ein Beispiel mit eingebautem Formatter
},
```

## Wie man Standard-Metadaten für Items festlegt

Sollen Items bei der Erstellung bestimmte Standard-Metadatenwerte haben? Zum Beispiel sollen neue Waffen mit 50 % Haltbarkeit starten? So geht's:

<Steps>
  <Step title="Adminmenü öffnen">
    Gib `/inventory` im Spiel ein, um das Adminmenü zu öffnen.
  </Step>
  <Step title="Item finden">
    Finde und klicke auf das Item, das du bearbeiten willst.
  </Step>
  <Step title="Metadata-Tab öffnen">
    Klicke auf den Tab "metadata".
  </Step>
  <Step title="Werte setzen">
    Setze die gewünschten Metadatenwerte.
  </Step>
</Steps>

### Erweitert – Templates für dynamische Metadaten nutzen

Manchmal willst du Metadaten, die sich abhängig von bestimmten Bedingungen ändern. Dafür kannst du Templates nutzen:

<Steps>
  <Step title="Metadata-Tab öffnen">
    Gehe zum selben Metadata-Tab im Item-Editor.
  </Step>
  <Step title="Zum Template-Typ wechseln">
    Ändere den Metadaten-Typ zu `template`.
  </Step>
  <Step title="Template wählen oder erstellen">
    Wähle entweder ein bestehendes Template oder erstelle dein eigenes in `jaksam_inventory/_data/metadata_templates.lua`.
  </Step>
</Steps>

Mit Templates kannst du Metadaten erstellen, die sich automatisch nach deinen eigenen Regeln aktualisieren!

#### Beispiel

Ein paar Beispiele, was mit dynamischen Metadata-Templates möglich ist:

- Einem Personalausweis-Item eines Spielers Name, Geburtsdatum, Größe usw. zuweisen
- Einer Waffe eine zufällige Haltbarkeit zuweisen
- Einem Item das Erstellungsdatum zuweisen (beim ersten Erstellen des Items)
