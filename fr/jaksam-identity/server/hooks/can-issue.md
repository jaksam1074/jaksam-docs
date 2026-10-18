---
title: "Peut délivrer"
description: "Décide qui peut délivrer un vrai document à un joueur."
icon: "user-check"
---

Appelé pour chaque délivrance qui a un émetteur : la commande admin et l'export [Délivrer](/fr/jaksam-identity/server/register/issue) avec `issuerSrc`. Pas appelé pour les mairies, les documents de départ ni la console. Renvoie `false` pour bloquer la délivrance (elle échoue avec `not_allowed`).

Modifie `Editable.CanIssue` dans `editable/server.lua` :

<CodeGroup>

```lua Function
function Editable.CanIssue(issuerSrc, targetSrc, typeId)
    return true
end
```

```lua Example
-- Only police officers may issue firearms permits (ESX)
function Editable.CanIssue(issuerSrc, targetSrc, typeId)
    if typeId == "weapon" then
        return ESX.GetPlayerFromId(issuerSrc).getJob().name == "police"
    end
    return true
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `issuerSrc` | integer | ID serveur du joueur qui le délivre |
| `targetSrc` | integer | ID serveur du joueur qui le reçoit |
| `typeId` | string | Le type de document, une clé de `Config.Documents` |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `allowed` | boolean | **true** pour autoriser la délivrance |
