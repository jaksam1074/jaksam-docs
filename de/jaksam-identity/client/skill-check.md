---
title: "Skill-Check"
description: "Das Skill-Check-Minispiel an den Fälscherstationen durch dein eigenes ersetzen."
icon: "gamepad"
---

Jede Fälscherstation führt einen Skill-Check aus: Ein Erfolg bringt der Fälschung Qualität, ein Fehlschlag kostet welche. Standardmäßig ist es `lib.skillCheck` aus ox_lib.

Bearbeite `Editable.SkillCheck` in `editable/client.lua`:

<CodeGroup>

```lua Function
function Editable.SkillCheck(difficulty)
    return lib.skillCheck(difficulty, { 'e' })
end
```

```lua Example
function Editable.SkillCheck(difficulty)
    -- one round of your own minigame per difficulty step
    for _ = 1, #difficulty do
        if not exports['my_minigame']:Start() then return false end
    end
    return true
end
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `difficulty` | table | Die Schwierigkeit aus `config/forgery.lua`: `Config.Forging.check.difficulty` (Standard `{ 'easy', 'medium' }`), oder `Config.Forging.emboss.difficulty` an der Prägemaschine |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | **true**, wenn der Spieler den Check bestanden hat |

Wie viel Qualität ein Erfolg bringt und ein Fehlschlag kostet, steht in `Config.Forging.check` und `Config.Forging.emboss` (`success`, `failure`).
