---
title: "Portefeuille RoadPhone"
description: "Affiche les documents qu'un joueur porte dans le portefeuille de RoadPhone, ou dans n'importe quel autre script de téléphone."
icon: "mobile-screen"
---

Si ton RoadPhone a le mode portefeuille `jksm_identity`, mets dans le `config.lua` de RoadPhone :

```lua
Config.Wallet = {
    Mode = 'jksm_identity',
    IdentityResource = 'jksm_identity',
    -- ...
}
```

Le portefeuille liste alors les documents que le joueur porte, avec photo et données imprimées. En montrer un ouvre la carte 3D pour l'autre joueur.

## Ce que liste le portefeuille

Comme un vrai portefeuille, seulement ce que le joueur a réellement sur lui :

- l'inventaire principal
- les conteneurs listés dans `Config.WalletContainers` (par défaut `{ 'wallet' }`), pas les piles d'ID

Un document faux ou volé affiche ce qui est imprimé dessus : le registre n'est jamais consulté.

<Info>
  - **ox_inventory :** un portefeuille ne compte que s'il est un conteneur ox (`setContainerProperties`) listé dans `Config.WalletContainers`.
  - **qb-inventory :** il n'a pas de conteneurs, le portefeuille ne lit donc que l'inventaire principal.
</Info>

## Autres scripts de téléphone

D'autres scripts de téléphone peuvent faire de même avec deux exports serveur :

- [Obtenir les documents du portefeuille](/fr/jaksam-identity/server/wallet/get-wallet-documents) : les documents que porte le joueur, sous forme de données de carte
- [Montrer un document](/fr/jaksam-identity/server/wallet/show-document) : montre un document porté à un joueur proche sous forme de carte 3D
