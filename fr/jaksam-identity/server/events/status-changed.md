---
title: "Statut modifié"
description: "Déclenché côté serveur après le changement de statut au registre d'un vrai document."
icon: "tag"
---

Cet event est déclenché après le changement de statut au registre d'un vrai document, par exemple quand il est déclaré volé dans une mairie ou suspendu avec l'export [Changer le statut](/fr/jaksam-identity/server/register/set-status).

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:statusChanged", function(serial, status, previous)

end)
```

```lua Example
AddEventHandler("jksm_identity:statusChanged", function(serial, status, previous)
    if status == "stolen" then
        -- flag it in your MDT
        exports["my_mdt"]:AddFlag(serial, "Reported stolen")
    end
end)
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string | Le numéro du document |
| `status` | string | Le nouveau statut : `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` ou `revoked` |
| `previous` | string | Le statut d'avant |
