---
title: "Obtenir les documents du portefeuille"
description: "Obtiens les documents qu'un joueur porte, sous forme de données de carte pour un portefeuille de téléphone."
icon: "wallet"
---

Renvoie les documents que le joueur a réellement sur lui : d'abord l'inventaire principal, puis les conteneurs de `Config.WalletContainers`. Un document faux ou volé affiche ce qui est imprimé dessus : le registre n'est jamais consulté.

<CodeGroup>

```lua Export
exports["jksm_identity"]:GetWalletDocuments(playerId)
```

```lua Example
lib.callback.register("my_phone:getWallet", function(source)
    local cards = {}
    for _, document in ipairs(exports["jksm_identity"]:GetWalletDocuments(source)) do
        cards[#cards + 1] = {
            serial = document.serial,
            title = document.title,
            name = document.firstname .. " " .. document.lastname,
            color = document.color,
            photo = document.photo,
        }
    end
    return cards
end)
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `playerId` | integer | ID serveur du joueur |

### Valeur de retour

Une liste de tables, une par document porté :

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `serial` | string | Le numéro du document |
| `type` | string | Le type de document, une clé de `Config.Documents` |
| `kind` | string | `identity`, `license` ou `badge` |
| `label` | string | Le libellé du document |
| `title` | string | Le titre de la carte selon le thème, par exemple `DRIVER LICENSE` |
| `color`, `accent` | string | Les couleurs du thème (hex) |
| `firstname`, `lastname`, `dob`, `sex` | string | L'identité imprimée |
| `classes` | string | Les catégories de licence imprimées |
| `rank` | string | Cartes de service uniquement : le grade imprimé |
| `issued`, `expires` | string | Les dates imprimées |
| `issuedAt`, `expiresAt` | integer \| nil | Les dates imprimées en temps unix |
| `valid` | boolean | Si la date d'expiration imprimée n'est pas passée. C'est ce que dit la carte, jamais le registre |
| `photo` | string \| nil | La photo en data URL, **nil** pour un document sans photo |
