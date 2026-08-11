---
title: "Item transferred"
description: "Hook, der ausgelöst wird, wenn ein Item zwischen Inventaren übertragen wird, inklusive Bewegungen innerhalb desselben Inventars."
icon: "right-left"
---

Wird ausgelöst, wenn ein Item zwischen Inventaren übertragen wird (inklusive Bewegungen innerhalb desselben Inventars, z.B. Ziehen innerhalb des gleichen Inventars). Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#register-a-hook) unter dem Event-Namen `onItemTransferred`.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | number | Der Spieler, der die Übertragung durchführt |
| `inventoryIdFrom` | string | Quell-Inventar-ID |
| `inventoryIdTo` | string | Ziel-Inventar-ID |
| `slotIdFrom` | number | Quell-Slot |
| `slotIdTo` | number | Ziel-Slot |
| `itemName` | string | z.B. `"weapon_pistol"` |
| `amount` | number | Übertragene Menge |
| `metadata` | table \| nil | Item-Metadaten |

### Beispiele

<AccordionGroup>
  <Accordion title="Polizeiwaffen im Spieler-Inventar blockieren">
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

  <Accordion title="Einfaches Crafting (Items zusammenziehen)">
    ```lua
    exports['jaksam_inventory']:registerHook("onItemTransferred", function(payload)
        local sourceItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdFrom, payload.slotIdFrom)
        local targetItem = exports["jaksam_inventory"]:getItemFromSlot(payload.inventoryIdTo, payload.slotIdTo)
        if not targetItem then return end -- Auf leeren Slot gezogen

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

Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für die `registerHook`-API, verfügbare Filter (inklusive der transferspezifischen `inventoryFromTypeFilter`/`inventoryToTypeFilter`/`intraInventoryOnly`) und das Rückgabewert-Verhalten.
