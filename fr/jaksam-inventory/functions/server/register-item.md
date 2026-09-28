---
title: "Register item"
description: "Enregistre une nouvelle définition d'objet à l'exécution (en mémoire uniquement, non sauvegardée dans un fichier)."
icon: "cube"
---

Enregistre une nouvelle définition d'objet à l'exécution (en mémoire uniquement, non sauvegardée dans un fichier). Seuls les champs sûrs et déclaratifs sont acceptés, tout le reste est rejeté à n'importe quelle profondeur.

<Note>
  Les objets enregistrés de cette façon seront perdus au redémarrage de la resource. Utilise ceci pour permettre à des scripts externes de définir leurs propres objets sans éditer `_data/items.lua`.
</Note>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerItem(itemName, itemData)
```

```lua Example: consumable
-- Enregistre un objet consommable simple
local success, err = exports['jaksam_inventory']:registerItem('energy_drink', {
    label = 'Energy Drink',
    weight = 0.3,
    stackable = true,
    maxStack = 10,
    description = 'Restores some energy',
    image = 'energy_drink.webp',
    consume = 1,
    status = { hunger = 5, thirst = 15 },
})

if not success then
    print('Failed to register item: ' .. err)
end
```

```lua Example: weapon
-- Enregistre un objet de type arme
local success, err = exports['jaksam_inventory']:registerItem('WEAPON_YOURWEAPON', {
    label = 'Custom Weapon',
    weight = 2.0,
    stackable = false,
    type = 'weapon',
    ammo = 'ammo_9mm',
    durability = 0.15,
    decay = true,
})
```

```lua Example: container
-- Enregistre un objet de type conteneur
local success, err = exports['jaksam_inventory']:registerItem('custom_bag', {
    label = 'Custom Bag',
    weight = 1.0,
    stackable = false,
    type = 'container',
    inventoryOptions = {
        maxSlots = 5,
        maxWeight = 10.0,
    },
})
```

</CodeGroup>

### Paramètres

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `itemName` | string | Identifiant unique de l'objet (ex. : `'custom_radio'`). Ne doit pas déjà exister dans le registre des objets |
| `itemData` | table | Table de définition de l'objet (voir les Notes ci-dessous pour les champs acceptés) |

### Valeur de retour

| Nom | Type de donnée | Description |
| --- | --- | --- |
| `success` | boolean | True si l'objet a été enregistré avec succès |
| `errorMessage` | string \| nil | Description de l'erreur si l'enregistrement a échoué |

### Notes

`itemData` n'accepte que les champs sûrs suivants ; tout autre champ est supprimé silencieusement :

**Champs obligatoires :** `label` (string), `weight` (number, >= 0), `stackable` (boolean)

**Champs optionnels :** `description`, `image`, `close`, `maxStack`, `rarity`, `type`, `customSymbol`, `ammo`, `durability`, `degrade`, `decay`, `consume`, `isGrenadeType`, `separateWeight`, `universal`, `oxClientEvent`, `oxClientExport`, `oxServerExport`

**Champs de type table optionnels** (validés récursivement, aucune fonction autorisée à l'intérieur) : `metadata`, `status`, `useOptions`, `inventoryOptions`, `throwableOptions`, `dynamicMetadata`

Aussi :

- Les objets enregistrés avec `registerItem` n'existent qu'en mémoire. Ils sont perdus au redémarrage de la resource. Si tu as besoin d'objets persistants, utilise le menu d'administration en jeu ou ajoute-les à `_data/items.lua`
- Les objets inconnus de l'inventaire ne sont jamais supprimés : ils sont masqués dans l'inventaire où ils se trouvent et reviennent automatiquement dès que l'objet est de nouveau enregistré ; ton script peut donc appeler `registerItem` à tout moment, généralement au démarrage de la resource
- Tu peux combiner `registerItem` avec `registerUsableItem` pour définir à la fois l'objet et son comportement d'utilisation depuis un script externe
- Si le nom de l'objet existe déjà, l'enregistrement est rejeté afin d'éviter d'écraser des objets définis par fichier
- Les champs de type table (comme `metadata`, `useOptions`, etc.) sont copiés en profondeur, donc les modifications apportées à la table d'origine après l'enregistrement n'ont aucun effet
