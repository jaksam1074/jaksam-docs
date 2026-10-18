---
title: "Obtenir les documents"
description: "Obtiens toutes les fiches du registre d'un personnage, les plus récentes d'abord."
icon: "list"
---

Renvoie les fiches du registre d'un personnage (vrais documents uniquement), les plus récentes d'abord.

<CodeGroup>

```lua Export
exports["jksm_identity"]:GetDocuments(identifier)
```

```lua Example
-- ESX
local identifier = ESX.GetPlayerFromId(playerId).identifier
-- QBCore / Qbox
-- local identifier = QBCore.Functions.GetPlayer(playerId).PlayerData.citizenid

for _, document in ipairs(exports["jksm_identity"]:GetDocuments(identifier)) do
    print(document.serial, document.doc_type, document.status)
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `identifier` | string | L'identifier du personnage. **Sur QBCore et Qbox, c'est le citizen ID** |

### Valeur de retour

Une liste de tables, vide si le personnage n'a aucun document :

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string | Le numéro du document |
| `doc_type` | string | Le type de document, une clé de `Config.Documents` |
| `firstname`, `lastname`, `dob`, `sex` | string | L'identité imprimée |
| `classes` | string | Les catégories de licence imprimées, par exemple `A, B` |
| `rank` | string | Cartes de service uniquement : le grade imprimé |
| `issued_at`, `expires_at` | integer | Temps unix. `expires_at` vaut **nil** pour les documents qui n'expirent jamais |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` ou `revoked` |
| `status_until` | integer | Temps unix de fin d'une suspension |
| `status_note` | string | La note gardée avec le statut |
