---
title: "Peut entrer dans l'atelier"
description: "Ajoute tes propres conditions pour entrer dans un atelier de faussaire."
icon: "door-open"
---

Appelé quand un joueur entre dans un atelier de faussaire. Que le joueur soit membre du job propriétaire, à partir du `minGrade` de l'atelier, est vérifié avant. Renvoie `false` pour le laisser dehors.

Modifie `Editable.CanEnterWorkshop` dans `editable/server.lua` :

<CodeGroup>

```lua Function
function Editable.CanEnterWorkshop(src, workshopId)
    return true
end
```

```lua Example
-- Nobody enters while wanted by the police
function Editable.CanEnterWorkshop(src, workshopId)
    return not exports["my_wanted"]:IsWanted(src)
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `src` | integer | ID serveur du joueur |
| `workshopId` | string | L'ID de l'atelier, une clé de `Config.Forgery.workshops` |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `allowed` | boolean | **true** pour laisser entrer le joueur |
