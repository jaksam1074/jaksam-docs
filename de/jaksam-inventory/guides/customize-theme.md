---
title: "Standard-Theme anpassen"
description: "Ein eigenes Standard-Theme für alle Spieler auf deinem Server festlegen, Schritt für Schritt"
icon: "palette"
---

Soll jeder Spieler das gleiche Standard-Theme haben? So geht's, Schritt für Schritt.

<Steps>
  <Step title="Öffne dein Inventar">
    Drücke **F2** im Spiel, um dein Inventar zu öffnen.
  </Step>
  <Step title="Öffne den Theme-Editor">
    Klicke auf den **Theme**-Button (unten rechts).

    <Frame>
      ![Inventory theme customization 1](/images/inventory-theme-1.jpg)
    </Frame>
  </Step>
  <Step title="Anpassen und speichern">
    Ändere die Farben und Stile nach Belieben und klicke auf **Speichern**.
  </Step>
  <Step title="Dein Theme auswählen">
    Stelle sicher, dass dein eigenes Theme ausgewählt ist.

    <Frame>
      ![Inventory theme customization 2](/images/inventory-theme-2.jpg)
    </Frame>
  </Step>
  <Step title="Konsole öffnen">
    Drücke **F8**, um die Konsole zu öffnen, und gib ein:

    ```bash
        admintheme
    ```
  </Step>
  <Step title="Theme-Code kopieren">
    Du siehst eine Menge Code.

    <Note>
      Kopiere _alles_ zwischen `COPY FROM THE LINE BELOW` und `COPY TILL THE LINE ABOVE`, achte darauf, die Ränder nicht zu verpassen.
    </Note>

    <Frame>
      ![Inventory theme customization 3](/images/inventory-theme-3.jpg)
    </Frame>
  </Step>
  <Step title="Theme-Datei öffnen">
    Gehe zu den Serverdateien und öffne:

    ```text
        jaksam_inventory/dist/assets/variables.css
    ```
  </Step>
  <Step title="Einfügen und ersetzen">
    Füge das Kopierte ein und ersetze **alles** in dieser Datei.
  </Step>
  <Step title="Neu starten">
    Starte das Script neu oder lade den Server neu.
  </Step>
</Steps>

<Tip>
  Das war's! Jetzt nutzt jeder standardmäßig deine eigenen Farben und Einstellungen (außer er ändert es selbst).
</Tip>
