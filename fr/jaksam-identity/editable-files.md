---
title: "Fichiers modifiables"
description: "Les fichiers de Jaksam Identity qui restent ouverts dans la version escrow : config, locales, bridge et hooks modifiables."
icon: "file-pen"
---

Jaksam Identity n'a pas de dossier `integrations`. Tout ce que tu peux modifier reste ouvert dans la version escrow, dans ces dossiers :

| Dossier | Contenu |
| --- | --- |
| `config/` | Tous les réglages |
| `locales/` | Textes, `Config.Locale` choisit la langue |
| `bridge/` | Inventaire, target, notifications, téléphone (le bridge du framework dans `bridge/framework/` est sous escrow) |
| `editable/` | Hooks : `CanIssue`, `OnIssued`, `CanEnterWorkshop`, `CanRaid`, `OnRaid`, `OnForged`, `OnLog`, `SkillCheck`, `Progress` |
| `install/` | Items d'inventaire, types d'items, images, SQL |

## Hooks modifiables

<CardGroup cols={2}>
  <Card title="editable/server.lua" icon="server" href="/fr/jaksam-identity/server/hooks">
    Hooks serveur : qui peut délivrer, entrer dans un atelier ou faire une descente, et ce qui se passe après une délivrance, un faux, une étape de descente ou une ligne de log.
  </Card>

  <Card title="editable/client.lua" icon="laptop" href="/fr/jaksam-identity/client">
    Hooks client : le skill check des postes de contrefaçon et la barre de progression.
  </Card>
</CardGroup>

Modifie le contenu selon ton serveur, mais **garde les noms des fonctions et les arguments**.

## Bridge

`Config.Bridge` dans `config/main.lua` choisit les fichiers de `bridge/` :

```lua
Config.Bridge = {
    framework = 'esx',          -- ESX version: 'esx' | QBCore version: 'auto' | 'qb' | 'qbox'
    inventory = 'jaksam',       -- 'jaksam' | 'ox_inventory' | 'qb-inventory' (QBCore version)
    target = 'ox_target',       -- 'ox_target' | QBCore version also 'qb-target' | 'auto'
    notify = 'esx',             -- 'esx' | 'qb' | 'qbox' | 'ox_lib' | QBCore version also 'auto'
    phone = 'roadphone',        -- 'roadphone' | 'none'
    menu = 'jksm',              -- 'jksm' (interaction card) | 'ox_lib' (context menu)
}
```

Pour prendre en charge un autre inventaire, le contrat qu'un bridge d'inventaire doit respecter est documenté en haut de `bridge/inventory/jaksam.lua`.
