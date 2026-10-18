---
title: "Pendant une descente"
description: "Envoie un appel au dispatch ou ta propre alarme quand une descente dans un atelier de faussaire avance."
icon: "tower-broadcast"
---

Appelé à chaque fois qu'une descente avance. C'est l'endroit pour ton appel au dispatch ou ta propre alarme.

Modifie `Editable.OnRaid` dans `editable/server.lua` :

<CodeGroup>

```lua Function
function Editable.OnRaid(workshopId, phase, src)

end
```

```lua Example
function Editable.OnRaid(workshopId, phase, src)
    if phase == "breach" then
        local workshop = Config.Forgery.workshops[workshopId]
        exports["my_dispatch"]:Alert({
            job = "police",
            title = "Raid in progress",
            message = ("Officers are breaching %s"):format(workshop and workshop.label or workshopId),
            coords = src and GetEntityCoords(GetPlayerPed(src)),
        })
    end
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `workshopId` | string | L'ID de l'atelier, une clé de `Config.Forgery.workshops` (les ateliers ajoutés en jeu y sont aussi) |
| `phase` | string | `breach` (un agent a commencé à enfoncer la porte), `aborted` (l'effraction a été abandonnée), `open` (la porte a cédé, les agents peuvent entrer), `over` (la descente est terminée, l'atelier est sous scellés) |
| `src` | integer \| nil | ID serveur de l'agent qui l'a fait, **nil** quand le temps s'est écoulé ou qu'un admin l'a fait |
