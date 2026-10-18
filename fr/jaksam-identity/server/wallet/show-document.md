---
title: "Montrer un document"
description: "Montre un document que porte le joueur à un joueur proche sous forme de carte 3D."
icon: "eye"
---

Montre à un autre joueur un document porté sous forme de carte 3D, exactement comme s'il était montré depuis l'inventaire. Le joueur doit porter le document, et les deux joueurs doivent être dans la même instance et dans `Config.ShowDistance`.

<CodeGroup>

```lua Export
exports["jksm_identity"]:ShowDocument(playerId, targetId, serial)
```

```lua Example
RegisterNetEvent("my_phone:showCard", function(targetId, serial)
    local ok, reason = exports["jksm_identity"]:ShowDocument(source, targetId, serial)
    if not ok then
        TriggerClientEvent("my_phone:notify", source, "Could not show the card: " .. reason)
    end
end)
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `playerId` | integer | ID serveur du joueur qui montre le document |
| `targetId` | integer | ID serveur du joueur qui le voit |
| `serial` | string | Le numéro d'un document que le joueur porte |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `ok` | boolean | **true** si la carte a été montrée |
| `reason` | string \| nil | `bad_target` (invalide ou même joueur), `too_far` (autre instance ou trop loin), `no_card` (le joueur ne porte pas ce document) |
