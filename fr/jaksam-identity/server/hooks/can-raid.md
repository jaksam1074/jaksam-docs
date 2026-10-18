---
title: "Peut faire une descente"
description: "Ajoute tes propres conditions pour enfoncer la porte d'un atelier de faussaire."
icon: "building-shield"
---

Appelé quand un agent commence à enfoncer la porte d'un atelier. L'unité et le grade, le service, assez d'agents connectés, l'item bélier et l'attente depuis la dernière descente sont vérifiés avant. Renvoie `false` pour bloquer l'effraction.

Modifie `Editable.CanRaid` dans `editable/server.lua` :

<CodeGroup>

```lua Function
function Editable.CanRaid(src, workshopId)
    return true
end
```

```lua Example
-- Raids need a warrant from your MDT
function Editable.CanRaid(src, workshopId)
    return exports["my_mdt"]:HasWarrant("workshop", workshopId)
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `src` | integer | ID serveur de l'agent |
| `workshopId` | string | L'ID de l'atelier, une clé de `Config.Forgery.workshops` |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `allowed` | boolean | **true** pour autoriser l'effraction |
