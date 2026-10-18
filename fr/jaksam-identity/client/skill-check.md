---
title: "Skill check"
description: "Remplace le mini-jeu de skill check des postes de contrefaçon par le tien."
icon: "gamepad"
---

Chaque poste de contrefaçon lance un skill check : une réussite ajoute de la qualité au faux, un échec en retire. Par défaut c'est `lib.skillCheck` d'ox_lib.

Modifie `Editable.SkillCheck` dans `editable/client.lua` :

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

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `difficulty` | table | La difficulté de `config/forgery.lua` : `Config.Forging.check.difficulty` (par défaut `{ 'easy', 'medium' }`), ou `Config.Forging.emboss.difficulty` à la machine à gaufrer |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `success` | boolean | **true** si le joueur a réussi le check |

Combien de qualité une réussite ajoute et un échec retire se règle dans `Config.Forging.check` et `Config.Forging.emboss` (`success`, `failure`).
