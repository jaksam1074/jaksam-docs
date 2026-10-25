---
title: "Minigames"
description: "Choose the hack and hotwire minigames of Boosting Creator, use external minigame scripts, or add your own."
icon: "gamepad"
---

Two minigames are chosen in **Settings > Theft** and **Settings > Tracker**:

- **Hotwire minigame**: played in the driver seat with **H**, when vehicles_keys is not running. Its difficulty is the class **Hotwire** setting.
- **Hack minigame**: played with **J** to hack the GPS tracker. It gets harder as the hacks go on.

## Available minigames

| Name | What it is | Needs |
| --- | --- | --- |
| `wires` | Drag each coloured wire to the terminal of the same colour (default hotwire) | |
| `signal` | Stop the moving needle on the signal, 3 hits, the car can still be driven (default hack) | |
| `skillcheck` | The skill check bar | |
| `progressbar` | A 5 second progress bar, always succeeds (hotwire only) | |
| `bruteforce` | Brute force hacking screen | |
| `datacrack` | | `datacrack` |
| `fingerprint` | | `utk_fingerprint` |
| `memory_game` | | `ultra-keypackhack` |

If an external minigame is in a folder with another name, set it in `EXTERNAL_SCRIPTS_NAMES` in `integrations/cl_integrations.lua`.

<Info>
  Every result is verified by the server. Suspicious attempts go to the Discord **cheat** log.
</Info>

## Add your own minigame

<Steps>
  <Step title="Copy the example">
    Copy `client/minigames/_EXAMPLE_MINIGAME.lua` in the same folder, with a new name, and remove the comment marks at the start and at the end.
  </Step>
  <Step title="Name it and call your script">
    Set `MINIGAME_NAME`. The function gets the difficulty (1 to 3) and must return `true` on success and `false` on failure:

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
  <Step title="Set the minimum time">
    If your minigame always takes a few seconds, add its shortest time in seconds to `minigamesMinSeconds` in `current_config.json`, next to the values already there:

    ```json
    "my_minigame": 3
    ```
  </Step>
  <Step title="Pick it">
    Restart the script. The new minigame appears in the **Hotwire minigame** list of the settings.

    The **Hack minigame** list is fixed: to hack with your own minigame, stop the script, set `"hackMinigame": "my_minigame"` in the `client` part of `current_config.json` and start it again.
  </Step>
</Steps>
