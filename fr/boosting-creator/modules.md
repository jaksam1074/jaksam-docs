---
title: "Modules"
description: "Remplace les fonctionnalités par défaut de Boosting Creator comme le dispatch, les clés des véhicules, les notifications, le text UI, la barre de progression et le skill check par tes propres modules."
icon: "puzzle-piece"
---

Les modules sont un moyen simple pour Boosting Creator de fonctionner avec les autres scripts de ton serveur : dispatch, clés des véhicules, notifications et plus.

Pour choisir un module existant, ouvre le menu `/boostingcreator`, va dans **Paramètres > Modules**, et sélectionne-le. Aussi simple que ça.

### Modules disponibles

| Catégorie | Options disponibles |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Keys | `none`, `qb-vehiclekeys`, `vehicles_keys` |
| Logs | `jaksam` |
| Notify | `default`, `ox_lib` |
| Progress Bar | `jaksam`, `ox_lib` |
| Skill Check | `jaksam`, `ox_lib` |
| Text UI | `esx`, `none`, `ox_lib` |

<Info>
  **Clés des véhicules** donne au voleur des clés temporaires de la voiture volée et les reprend quand le contrat se termine. Avec `vehicles_keys` en route, la voiture est aussi crochetée et démarrée aux fils avec vehicles_keys à la place de l'effraction et du démarrage aux fils du script.
</Info>

### Créer un module personnalisé

<Steps>
  <Step title="Va dans le dossier des modules">
    Va dans le dossier `boosting_creator/_modules/<category>`, par exemple `_modules/dispatch`.
  </Step>
  <Step title="Duplique un module existant">
    Copie un module existant (par exemple `default`) et colle-le dans le même dossier comme modèle.
  </Step>
  <Step title="Renomme la copie">
    Renomme le dossier et le `moduleName` dans ses fichiers pour qu'ils correspondent au script que tu intègres.
  </Step>
  <Step title="Implémente les fonctions">
    Modifie les fonctions pour qu'elles appellent ton script. Pour un dispatch :

    ```lua
    local moduleType = "dispatch"
    local moduleName = "yourModuleName"

    -- Don't touch, required to appear in the in-game settings
    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Server side, once per alert
    Integrations[moduleType][moduleName].alertPoliceServerSide = function(coords, message, category)
        if not IsDuplicityVersion() then return end

        -- Call your dispatch script's export or event here
    end
    ```

    Les fonctions dont chaque catégorie a besoin :

    | Catégorie | Fonctions |
    | --- | --- |
    | Dispatch | `alertPoliceServerSide`, `alertPoliceMemberClientSide` |
    | Keys | `giveKeys`, `removeKeys` |
  </Step>
  <Step title="Redémarre et choisis-le">
    Redémarre le script, puis choisis ton module dans **Paramètres > Modules**.
  </Step>
</Steps>
