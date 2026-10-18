---
title: "Barre de progression"
description: "Remplace la barre de progression utilisée pour enfoncer une porte, saisir des preuves et les détruire."
icon: "spinner"
---

Tout ce qui prend du temps et peut être abandonné (enfoncer une porte, saisir, détruire des preuves) passe par une seule fonction. Par défaut c'est `lib.progressBar` d'ox_lib.

Modifie `Editable.Progress` dans `editable/client.lua` :

<CodeGroup>

```lua Function
function Editable.Progress(seconds, label)
    return lib.progressBar({
        duration = seconds * 1000, label = label, useWhileDead = false, canCancel = true,
        disable = { move = true, car = true, combat = true },
        anim = { dict = 'mini@repair', clip = 'fixing_a_player' },
    }) == true
end
```

```lua Example
function Editable.Progress(seconds, label)
    return exports['my_progressbar']:Start({
        time = seconds * 1000,
        text = label,
        cancelable = true,
    })
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `seconds` | number | La durée de l'action |
| `label` | string | Le texte affiché avec la barre de progression |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `completed` | boolean | **true** quand elle est allée jusqu'au bout, **false** quand le joueur l'a annulée |
