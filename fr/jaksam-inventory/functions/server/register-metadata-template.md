---
title: "Register metadata template"
description: "Ajoute un template de metadata depuis un script externe, utilisé par les items avec des metadata dynamiques."
icon: "tags"
---

Ajoute un template de metadata depuis un script externe. Un template de metadata est une fonction qui génère une valeur de metadata chaque fois qu'un item qui l'utilise est ajouté à un inventaire (un numéro de série, le nom du propriétaire, une statistique aléatoire, etc.).

Les templates enregistrés ainsi fonctionnent exactement comme ceux de `metadata_templates.lua` : ils apparaissent dans l'éditeur d'items du menu admin `/inventory`, où tu peux les assigner à n'importe quel item. Consulte le [guide Metadata](/fr/jaksam-inventory/guides/metadata) pour savoir comment assigner les templates aux items.

<Note>
  Les templates sont gardés en mémoire uniquement. Ils sont retirés quand ton script s'arrête et perdus quand jaksam_inventory redémarre, donc enregistre-les à chaque démarrage de ton script.
</Note>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerMetadataTemplate(templateId, cb)
```

```lua Example
local function registerTemplates()
    exports['jaksam_inventory']:registerMetadataTemplate('my_serial', function(playerId, inventoryId, itemName, amount, metadata, slotId)
        return 'SN-' .. math.random(100000, 999999)
    end)
end

-- Enregistrer au démarrage, et à nouveau si jaksam_inventory redémarre après ton script
registerTemplates()

AddEventHandler('onResourceStart', function(resourceName)
    if resourceName == 'jaksam_inventory' then registerTemplates() end
end)
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `templateId` | string | L'ID du template, celui que tu choisis dans l'éditeur d'items |
| `cb` | function | Appelée chaque fois qu'un item utilisant le template est ajouté. Sa valeur de retour devient la valeur de la metadata |

#### Paramètres du callback

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `playerId` | number \| nil | ID serveur du joueur, uniquement quand l'item est ajouté à l'inventaire d'un joueur |
| `inventoryId` | string | L'inventaire auquel l'item est ajouté |
| `itemName` | string | L'item ajouté |
| `amount` | number | La quantité ajoutée |
| `metadata` | table \| nil | Les metadata avec lesquelles l'item est ajouté |
| `slotId` | string \| nil | Le slot où l'item est ajouté, s'il a été précisé |

### Valeur de retour

Aucune

### Notes

- Côté serveur uniquement, car les metadata sont toujours générées par le serveur
- Si l'ID de ton template est le même que celui d'un template de `metadata_templates.lua`, le tien le remplace tant que ton script tourne, et l'original revient quand ton script s'arrête
- Tant qu'un template n'est pas enregistré (ton script n'a pas encore démarré, ou s'est arrêté), les items qui l'utilisent sont ajoutés normalement, simplement sans ce champ de metadata, et la console du serveur affiche un avertissement
