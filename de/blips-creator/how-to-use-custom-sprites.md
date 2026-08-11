---
title: "Wie man eigene Sprites nutzt"
description: "Die Standard-Blip-Sprites durch eigene Symbole ersetzen."
icon: "image"
---

Blips Creator bietet eine extrem einfache Möglichkeit, Blip-Sprites zu ersetzen.

<Steps>
  <Step title="Ein Symbol wählen">
    Wähle ein `.png`-Symbol, das du nutzen willst (64x64px ist am besten).
  </Step>
  <Step title="Den Sprites-Ordner öffnen">
    Gehe zum Ordner `blips_creator/_sprites/REPLACEABLE`.
  </Step>
  <Step title="Den zu ersetzenden Sprite markieren">
    Wähle einen zu ersetzenden Sprite, kopiere seinen Namen und füge ein `#` vor den Namen ein (damit du ihn bei Bedarf später leichter wiederfindest).
  </Step>
  <Step title="Dein Symbol hinzufügen">
    Lege das neue Symbol mit dem gleichen Namen wie der alte Sprite ab.
  </Step>
  <Step title="Script neu starten">
    Starte Blips Creator **2 Mal** neu.
  </Step>
</Steps>

## Beispiel mit Bildern

In diesem Beispiel wird das grüne Logo durch den roten Sprite ersetzt.

<Frame caption="Ordner blips_creator/_sprites/REPLACEABLE">
  ![REPLACEABLE folder](/images/immagine-1.png)
</Frame>

<Frame caption="Dateinamen kopieren">
  ![Copy the file name](/images/immagine-8.png)
</Frame>

<Frame caption='Ein "#" vor den Namen setzen'>
  ![Add a hash before the name](/images/immagine-2.png)
</Frame>

<Frame caption="Deine neue Symboldatei umbenennen">
  ![Rename the new icon file](/images/immagine-4.png)
</Frame>

<Frame caption="Endergebnis">
  ![Final result](/images/immagine-7.png)
</Frame>

Starte das Script jetzt **2 Mal** neu, dann ist der Sprite aktualisiert.
