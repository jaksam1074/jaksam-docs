---
title: "Changer le statut"
description: "Change le statut au registre d'un vrai document : perdu, volé, saisi, suspendu, remplacé, retiré ou valide."
icon: "tag"
---

Change le statut au registre d'un vrai document. Le changement est enregistré dans le log et déclenche l'event [Statut modifié](/fr/jaksam-identity/server/events/status-changed).

<CodeGroup>

```lua Export
exports["jksm_identity"]:SetStatus(serial, status, options)
```

```lua Example
-- Suspend a driver licence for 7 days from an MDT
local ok, reason = exports["jksm_identity"]:SetStatus("SAAB1234567", "suspended", {
    untilTime = os.time() + 7 * 24 * 60 * 60,
    note = "Speeding, 7 days",
    actor = officerIdentifier,
})

if not ok then print("Failed: " .. reason) end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string | Le numéro du document |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` ou `revoked` |
| `options` | table (optionnel) | Voir plus bas |

### Options

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `untilTime` | integer | Seulement avec `suspended` : temps unix de fin de la suspension. Ensuite le contrôle du registre renvoie de nouveau `valid` |
| `note` | string | Une note gardée avec le statut (jusqu'à 255 caractères) |
| `actor` | string | Qui l'a changé, écrit dans le log admin |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `ok` | boolean | **true** si le statut a été changé |
| `reason` | string \| nil | `bad_arguments` ou `not_found` (le numéro n'est pas un vrai document) |
