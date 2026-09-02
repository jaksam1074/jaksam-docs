---
title: "Item transferred"
description: "Hook déclenché quand un item est transféré entre inventaires, y compris les déplacements intra-inventaire."
icon: "right-left"
---

Se déclenche quand un item est transféré entre inventaires (y compris les déplacements intra-inventaire, par exemple glisser dans le même inventaire). Enregistre-le avec [`registerHook`](/fr/jaksam-inventory/hooks#enregistrer-un-hook) en utilisant le nom d'event `onItemTransferred`.

### Payload

| Champ | Type de donnée | Description |
| --- | --- | --- |
| `playerId` | number | Le joueur effectuant le transfert |
| `inventoryIdFrom` | string | ID de l'inventaire source |
| `inventoryIdTo` | string | ID de l'inventaire de destination |
| `slotIdFrom` | number | Slot source |
| `slotIdTo` | number | Slot de destination |
| `itemName` | string | par exemple `"weapon_pistol"` |
| `amount` | number | Quantité transférée |
| `metadata` | table \| nil | Métadonnées de l'item |

<Note>
  L'inventaire admin (omnipack) ne déclenche **pas** ce hook, il a son propre [`onOmnipackTransaction`](/fr/jaksam-inventory/hooks/on-omnipack-transaction). Ainsi les restrictions que tu écris pour tes joueurs ne s'appliquent jamais à un admin qui crée un item.
</Note>

### Exemples

<AccordionGroup>
  <Accordion title="Bloquer les armes de police dans l'inventaire du joueur">
    ```lua
    exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
        local item = exports["jaksam_inventory"]:getStaticItem(payload.itemName)
        if item and item.policeOnly then
            return false, "Only police can have this weapon"
        end
    end, {
        itemTypeFilter = {weapon = true},
        inventoryToTypeFilter = {player = true}
    })
    ```
  </Accordion>

  <Accordion title="Craft simple (glisser des items ensemble)">
    ```lua
    exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
        local sourceItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdFrom, payload.slotIdFrom)
        local targetItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdTo, payload.slotIdTo)
        if not targetItem then return end -- Glissé sur un slot vide

        if sourceItem.name == "bread" and targetItem.name == "meat" then
            exports["jaksam_inventory"]:removeItem(payload.inventoryIdFrom, "bread", 1, payload.slotIdFrom)
            exports["jaksam_inventory"]:removeItem(payload.inventoryIdFrom, "meat", 1, payload.slotIdTo)
            exports["jaksam_inventory"]:addItem(payload.inventoryIdFrom, "sandwich", 1)
            return false, "You crafted a sandwich", "success"
        end
    end, {intraInventoryOnly = true})
    ```
  </Accordion>
</AccordionGroup>

Voir [l'aperçu des Hooks](/fr/jaksam-inventory/hooks) pour l'API `registerHook`, les filtres disponibles (y compris les filtres spécifiques au transfert `inventoryFromTypeFilter`/`inventoryToTypeFilter`/`intraInventoryOnly`), et le comportement des valeurs de retour.
