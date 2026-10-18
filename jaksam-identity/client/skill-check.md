---
title: "Skill check"
description: "Replace the skill check minigame at the forging stations with your own."
icon: "gamepad"
---

Every forging station runs a skill check: a success adds quality to the forgery, a failure takes it. By default it is `lib.skillCheck` from ox_lib.

Edit `Editable.SkillCheck` in `editable/client.lua`:

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `difficulty` | table | The difficulty from `config/forgery.lua`: `Config.Forging.check.difficulty` (default `{ 'easy', 'medium' }`), or `Config.Forging.emboss.difficulty` at the embosser |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `success` | boolean | **true** if the player passed the check |

How much quality a success adds and a failure takes is set in `Config.Forging.check` and `Config.Forging.emboss` (`success`, `failure`).
