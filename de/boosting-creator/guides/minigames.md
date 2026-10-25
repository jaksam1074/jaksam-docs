---
title: "Minispiele"
description: "Die Hack- und Kurzschluss-Minispiele von Boosting Creator wählen, externe Minispiel-Scripts nutzen oder eigene hinzufügen."
icon: "gamepad"
---

Zwei Minispiele werden unter **Einstellungen > Diebstahl** und **Einstellungen > Tracker** gewählt:

- **Minispiel zum Kurzschließen**: wird auf dem Fahrersitz mit **H** gespielt, wenn vehicles_keys nicht läuft. Seine Schwierigkeit ist die Einstellung **Kurzschließen** der Klasse.
- **Hack-Minispiel**: wird mit **J** gespielt, um den GPS-Tracker zu hacken. Es wird mit jedem Hack schwerer.

## Verfügbare Minispiele

| Name | Was es ist | Braucht |
| --- | --- | --- |
| `wires` | Jedes farbige Kabel auf den Anschluss derselben Farbe ziehen (Standard zum Kurzschließen) | |
| `signal` | Die bewegliche Nadel auf dem Signal stoppen, 3 Treffer, das Auto bleibt fahrbar (Standard zum Hacken) | |
| `skillcheck` | Die Skill-Check-Leiste | |
| `progressbar` | Ein Fortschrittsbalken von 5 Sekunden, gelingt immer (nur Kurzschließen) | |
| `bruteforce` | Brute-Force-Hacking-Bildschirm | |
| `datacrack` | | `datacrack` |
| `fingerprint` | | `utk_fingerprint` |
| `memory_game` | | `ultra-keypackhack` |

Liegt ein externes Minispiel in einem Ordner mit anderem Namen, trage ihn in `EXTERNAL_SCRIPTS_NAMES` in `integrations/cl_integrations.lua` ein.

<Info>
  Jedes Ergebnis wird vom Server geprüft. Verdächtige Versuche gehen in den Discord-Log **cheat**.
</Info>

## Eigenes Minispiel einbauen

<Steps>
  <Step title="Das Beispiel kopieren">
    Kopiere `client/minigames/_EXAMPLE_MINIGAME.lua` im selben Ordner unter einem neuen Namen und entferne die Kommentarzeichen am Anfang und am Ende.
  </Step>
  <Step title="Benennen und dein Script aufrufen">
    Setze `MINIGAME_NAME`. Die Funktion bekommt die Schwierigkeit (1 bis 3) und muss `true` bei Erfolg und `false` bei Misserfolg zurückgeben:

    ```lua
    Minigames = Minigames or { registry = {} }
    local MINIGAME_NAME <const> = "my_minigame"

    Minigames.registry[MINIGAME_NAME] = function(difficulty)
        local promise = promise.new()

        TriggerEvent("my_minigame:start", difficulty, function(result)
            promise:resolve(result)
        end)

        return Citizen.Await(promise)
    end
    ```
  </Step>
  <Step title="Die Mindestzeit festlegen">
    Wenn dein Minispiel immer ein paar Sekunden dauert, trag seine kürzeste Dauer in Sekunden in `minigamesMinSeconds` in `current_config.json` ein, neben den Werten, die schon da sind:

    ```json
    "my_minigame": 3
    ```
  </Step>
  <Step title="Auswählen">
    Starte das Script neu. Das neue Minispiel erscheint in der Liste **Minispiel zum Kurzschließen** der Einstellungen.

    Die Liste **Hack-Minispiel** ist fest: Um mit deinem eigenen Minispiel zu hacken, stoppe das Script, setze `"hackMinigame": "my_minigame"` im `client`-Teil von `current_config.json` und starte es wieder.
  </Step>
</Steps>
