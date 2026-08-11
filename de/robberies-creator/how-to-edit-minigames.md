---
title: "Wie man Minigames bearbeitet"
description: "Ein eigenes Minigame zu Robberies Creator hinzufügen."
icon: "gamepad"
---

Du kannst jedes beliebige Minigame hinzufügen, dafür brauchst du aber ein Mindestmaß an Programmierkenntnissen.

<Steps>
  <Step title="Deine Minigame-Datei erstellen">
    Füge deine Minigame-Datei in `integrations/minigames` hinzu und erstelle deine Funktion (nutze `datacrack.lua` oder ein anderes bestehendes Minigame als Beispiel).
  </Step>
  <Step title="Das Minigame registrieren">
    Bearbeite die Datei `integrations/cl_hack_minigame.lua`, um dein Minigame zu unterstützen.
  </Step>
  <Step title="Zur UI hinzufügen">
    Bearbeite `html/index.js`, suche nach `"datacrack"` und füge dort ebenfalls dein Minigame hinzu.
  </Step>
</Steps>
