---
title: "Délivrer"
description: "Délivre un vrai document à un joueur et le met dans son inventaire."
icon: "id-card"
---

Délivre un vrai document : l'écrit au registre, prend la photo, met l'item dans l'inventaire du joueur et marque `replaced` l'ancien document valide du même type.

<CodeGroup>

```lua Export
exports["jksm_identity"]:Issue(playerId, typeId, options)
```

```lua Example
-- A DMV script issuing the driver licence after a passed test
local serial, reason = exports["jksm_identity"]:Issue(playerId, "drive", {
    issuerSrc = instructorId,
    grant = { "drive" },
})

if serial then
    print("Issued driver licence " .. serial)
else
    print("Not issued: " .. reason)
end
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `playerId` | integer | ID serveur du joueur qui reçoit le document |
| `typeId` | string | Le type de document, une clé de `Config.Documents` (par exemple `id_card`, `drive`, `weapon`, `badge_pd`) |
| `options` | table (optionnel) | Voir plus bas |

### Options

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `issuerSrc` | integer | ID serveur du joueur qui le délivre. `Editable.CanIssue` est consulté d'abord, et l'émetteur est écrit au registre. `0` désigne la console |
| `grant` | table | Types de licence à donner au personnage avant la délivrance, par exemple `{ "drive", "drive_truck" }`. Doivent être des licences de ce document |
| `force` | boolean | Délivre même si la licence (documents `license`) ou le job (documents `badge`) manque |
| `photo` | boolean | `false` pour délivrer sans prendre de photo |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string \| nil | Le nouveau numéro de document, ou **nil** s'il n'a pas été délivré |
| `reason` | string \| nil | Pourquoi il n'a pas été délivré : `unknown_type`, `no_player`, `not_allowed`, `license_missing`, `wrong_job`, `busy` (une photo de ce joueur est en cours), `additem_<code>` (l'inventaire a refusé l'item) |

<Note>
  La photo est prise sur le personnage du joueur, l'appel l'attend donc. Appelle-le depuis un thread ou un event handler, pas depuis du code qui doit rendre la main tout de suite.
</Note>
