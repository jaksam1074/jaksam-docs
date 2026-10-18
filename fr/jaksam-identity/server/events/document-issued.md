---
title: "Document délivré"
description: "Déclenché côté serveur après la délivrance d'un vrai document."
icon: "id-card"
---

Cet event est déclenché après la délivrance d'un vrai document : dans une mairie, comme document de départ, par esx_dmvschool ou la mairie de QBCore, par la commande admin ou par l'export [Délivrer](/fr/jaksam-identity/server/register/issue).

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:issued", function(serial, typeId, targetSrc, issuerSrc)

end)
```

```lua Example
AddEventHandler("jksm_identity:issued", function(serial, typeId, targetSrc, issuerSrc)
    if typeId == "weapon" then
        print(("Player %d received firearms permit %s"):format(targetSrc, serial))
    end
end)
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string | Le nouveau numéro de document |
| `typeId` | string | Le type de document, une clé de `Config.Documents` |
| `targetSrc` | integer | ID serveur du joueur qui l'a reçu |
| `issuerSrc` | integer \| nil | ID serveur du joueur qui l'a délivré, `0` pour la console, **nil** quand personne ne l'a délivré (mairie, document de départ) |

<Tip>
  Les mêmes arguments arrivent à `Editable.OnIssued` dans `editable/server.lua`, si tu préfères garder ton code là.
</Tip>
