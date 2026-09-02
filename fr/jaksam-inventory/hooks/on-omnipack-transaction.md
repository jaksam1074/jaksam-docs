---
title: "Omnipack transaction"
description: "Hook déclenché quand un admin crée ou détruit un item via l'inventaire admin (omnipack)."
icon: "user-shield"
---

Se déclenche quand un admin sort un item de l'[inventaire admin (omnipack)](/fr/jaksam-inventory/guides/admin-inventory), ce qui le crée, ou en glisse un dedans, ce qui le détruit. Ce hook peut annuler l'opération. Enregistre-le avec [`registerHook`](/fr/jaksam-inventory/hooks#enregistrer-un-hook) en utilisant le nom d'event `onOmnipackTransaction`.

C'est le seul hook qui sait **quel** admin l'a fait, c'est donc celui à utiliser pour logger les items créés par les admins.

### Payload

| Champ | Type de donnée | Description |
| --- | --- | --- |
| `playerId` | number | L'admin qui utilise l'inventaire admin |
| `action` | string | `"spawn"` (item créé) ou `"delete"` (item détruit) |
| `inventoryId` | string | L'autre inventaire : là où l'item va, ou d'où il vient |
| `slotId` | number | Le slot concerné dans l'autre inventaire |
| `itemName` | string | par exemple `"weapon_pistol"` |
| `amount` | number | Quantité créée ou détruite |
| `metadata` | table \| nil | Métadonnées de l'item |

<Note>
  L'inventaire admin ne déclenche **pas** [`onItemTransferred`](/fr/jaksam-inventory/hooks/on-item-transferred), il ne déclenche que ce hook. Ainsi les restrictions que tu écris pour tes joueurs ne s'appliquent jamais à un admin qui crée un item.
</Note>

**Filtres disponibles :** `itemNameFilter`, `itemTypeFilter`, `inventoryTypeFilter` et `inventoryFilter` - les deux derniers s'appliquent à `inventoryId`, l'omnipack lui-même n'est donc jamais ce sur quoi tu filtres.

### Exemples

<AccordionGroup>
  <Accordion title="Logger ce que les admins créent depuis l'inventaire admin">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        print(("[ADMIN] %s (%s) %sed %dx %s - inventory: %s"):format(
            GetPlayerName(payload.playerId), payload.playerId, payload.action,
            payload.amount, payload.itemName, payload.inventoryId))
    end)
    ```
  </Accordion>

  <Accordion title="Empêcher les admins de créer un item précis">
    ```lua
    exports['jaksam_inventory']:registerHook("onOmnipackTransaction", function(payload)
        if payload.action ~= "spawn" then return end -- Le supprimer ne pose pas de problème

        return false, "This item can't be spawned from the admin inventory"
    end, {
        itemNameFilter = {money = true}
    })
    ```
  </Accordion>
</AccordionGroup>

Voir [l'aperçu des Hooks](/fr/jaksam-inventory/hooks) pour l'API `registerHook`, les filtres disponibles et le comportement des valeurs de retour.
