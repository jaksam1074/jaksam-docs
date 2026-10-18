---
title: "Cartes de visite"
description: "Laisse chaque job imprimer ses propres cartes de visite avec nom, titre, numéro de téléphone et une ligne libre."
icon: "address-card"
---

Chaque job imprime ses propres cartes de visite, avec son propre design. Les joueurs ouvrent la fenêtre d'impression avec `/businesscards` et reçoivent une pile de cartes avec :

- leur nom
- un titre modifiable
- leur numéro de téléphone (prérempli depuis RoadPhone quand `Config.Bridge.phone = 'roadphone'`)
- une ligne libre

Les cartes de visite n'ont ni registre ni numéro. Une carte de visite peut être regardée, montrée ou donnée au joueur le plus proche.

## Configuration

`Config.BusinessCards` dans `config/business.lua` :

```lua
Config.BusinessCards = {
    item = 'business_card',
    command = 'businesscards',   -- opens the print dialog
    amount = 10,                 -- cards per print
    price = 50,                  -- cash per print
    maxTitle = 32,
    maxPhone = 20,
    maxText = 60,
    excludeJobs = { unemployed = true },
    jobs = {
        police = { title = 'LOS SANTOS POLICE DEPARTMENT', header = 'To Protect and to Serve', emblem = 'shield', primary = '#0b1f3a', secondary = '#f5f6f8', accent = '#d4af37' },
    },
    default = { header = 'Los Santos', emblem = 'star', primary = '#2b3440', secondary = '#f6f6f4', accent = '#c8a24a' },
}
```

Un job sans entrée dans `jobs` reçoit le design `default` avec le libellé de son job comme titre. Les jobs de `excludeJobs` ne peuvent pas imprimer.

<Info>
  Pour afficher un numéro de téléphone d'un autre script de téléphone, modifie `bridge/phone.lua`. Voir [Numéro de téléphone](/fr/jaksam-identity/server/hooks/phone-number).
</Info>
