---
title: "Wie man Minigames hinzufügt"
description: "Ein eigenes Minigame zu Missions Creator hinzufügen."
icon: "gamepad"
---

Neue Minigames hinzuzufügen ist einfach. Folge diesem Ablauf, um ein neues Minigame hinzuzufügen:

<Steps>
  <Step title="Beispieldatei duplizieren">
    Dupliziere die Datei `missions_creator/client/minigames/_EXAMPLE_MINIGAME.lua`.
  </Step>
  <Step title="Datei umbenennen">
    Benenne die Datei nach dem Namen deines Minigames um.
  </Step>
  <Step title="Kommentarmarkierungen entfernen">
    Öffne die neue Datei und entferne die Kommentare am Anfang und am Ende der Datei (entferne die Symbole `--[[` und `--]]`).
  </Step>
  <Step title="Minigame umbenennen">
    Ändere `YOUR_MINIGAME_NAME` zum Namen deines Minigames.
  </Step>
  <Step title="Dein Minigame implementieren">
    Bearbeite die Funktion, um dein Minigame zu unterstützen. Sie muss bei Erfolg `true` und bei Misserfolg `false` zurückgeben. Beispiele findest du in `datacrack.lua`, `fingerprint.lua` und `memory_game.lua`.
  </Step>
  <Step title="Script neu starten">
    Speichere die Datei und starte das Script neu. War alles korrekt (insbesondere die Implementierung des Minigames selbst), solltest du dein Minigame in der Liste der Minigames des Scripts sehen.
  </Step>
</Steps>
