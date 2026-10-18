---
title: "Contrôler"
description: "Contrôle au registre d'un numéro de document, comme le voit une autorité."
icon: "magnifying-glass"
---

Renvoie ce que voit une autorité quand elle contrôle un document au registre. Ne révèle jamais qui a fait un faux ni sa qualité.

<CodeGroup>

```lua Export
exports["jksm_identity"]:Check(serial, printed)
```

```lua Example
-- MDT lookup of the card a suspect handed over
local result = exports["jksm_identity"]:Check(item.metadata.serial, {
    firstname = item.metadata.firstname,
    lastname = item.metadata.lastname,
    dob = item.metadata.dob,
})

if not result.found then
    print(result.personExists and "Serial does not match this person" or "No such person")
elseif #result.problems > 0 then
    print("Problems: " .. table.concat(result.problems, ", "))
else
    print("Document is valid")
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string | Le numéro du document |
| `printed` | table (optionnel) | Ce qui est imprimé sur la carte : `{ firstname, lastname, dob }`. Sert à distinguer un mauvais numéro d'une personne qui n'existe pas, et à repérer des données imprimées différentes du registre |

### Valeur de retour

Une table :

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `found` | boolean | **true** si le numéro est dans le registre (un vrai document) |
| `personExists` | boolean | Seulement quand `found` vaut **false** : si un personnage avec le nom imprimé existe |
| `status` | string | Seulement si trouvé : `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` ou `revoked`. Une suspension terminée renvoie `valid` |
| `problems` | table | Liste de strings, vide si tout va bien (voir plus bas) |
| `record` | table | Seulement si trouvé : la ligne du registre (`serial`, `doc_type`, `owner`, `firstname`, `lastname`, `dob`, `sex`, `classes`, `issued_at`, `expires_at`, `status`, `status_until`, `status_note`, ...) |
| `currentClasses` | string | Seulement pour les documents avec catégories : les catégories que le propriétaire détient maintenant, par exemple `A, B` |

### Problèmes

| Problème | Signification |
| --- | --- |
| `person_not_found` | Pas dans le registre, et aucun personnage avec le nom imprimé n'existe |
| `serial_mismatch` | Pas dans le registre, mais un personnage avec le nom imprimé existe |
| `lost`, `stolen`, `seized`, `suspended`, `replaced`, `revoked` | Le statut du document |
| `expired` | La date d'expiration est passée |
| `license_missing` | Le propriétaire n'a plus la licence (ni aucune de ses catégories) |
| `class_revoked:<class>` | Une catégorie imprimée sur la carte n'est plus détenue, par exemple `class_revoked:C` |
| `left_job` | Le propriétaire de la carte de service n'a plus le job |
| `data_mismatch` | Le nom ou la date de naissance imprimés ne correspondent pas au registre |
