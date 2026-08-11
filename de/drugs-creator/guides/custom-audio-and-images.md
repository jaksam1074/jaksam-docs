---
title: "Wie man eigene Audiodateien und Bilder zu Effekten hinzufügt"
description: "Füge deine eigene Musik oder Bilder zu Drogen-Effekten hinzu, indem du Dateien in den richtigen Ordner legst."
icon: "photo-film"
---

<Tip>
  Willst du deine eigene Musik oder Bilder zu Drogen-Effekten hinzufügen? Leg einfach Dateien in den richtigen Ordner.
</Tip>

Das Script scannt automatisch die Asset-Ordner und zeigt alle gültigen Dateien im Effekt-Editor-Dropdown. Keine Code-Änderungen nötig.

## Eigene Audiodateien hinzufügen

<Steps>
  <Step title="Zum Audio-Ordner navigieren">
    Öffne deine Serverdateien und navigiere zu `drugs_creator/html/assets/audio/`.
  </Step>
  <Step title="Deine Dateien hinzufügen">
    Lege deine Audiodateien in diesem Ordner ab.
  </Step>
  <Step title="Neu starten">
    Starte das Script oder den Server neu.
  </Step>
</Steps>

Das war's! Die neuen Audiodateien erscheinen jetzt im **Music**-Effekt-Dropdown beim Bearbeiten von Drogen-Effekten.

### Unterstützte Audioformate

`mp3`, `ogg`, `wav`, `flac`, `aac`, `m4a`

## Eigene Bilder hinzufügen

<Steps>
  <Step title="Zum Bilder-Ordner navigieren">
    Öffne deine Serverdateien und navigiere zu `drugs_creator/html/assets/img/`.
  </Step>
  <Step title="Deine Dateien hinzufügen">
    Lege deine Bilddateien in diesem Ordner ab.
  </Step>
  <Step title="Neu starten">
    Starte das Script oder den Server neu.
  </Step>
</Steps>

Die neuen Bilder erscheinen in den Dropdowns **Trip Screen Image** und **3D World Image**.

### Unterstützte Bildformate

`jpg`, `jpeg`, `png`, `gif`, `webp`

## Wichtige Hinweise

- Dateinamen werden direkt als Beschriftung im Dropdown verwendet, nutze also aussagekräftige Namen (z.B. `space_trip.jpg` statt `img1.jpg`)
- Fügst du Dateien hinzu, während der Server läuft, starte das Script neu, damit die Änderungen erscheinen
- Halte Dateigrößen angemessen, große Bilder oder Audiodateien können die Ladezeiten für Spieler beeinträchtigen
