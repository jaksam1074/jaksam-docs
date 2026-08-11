---
title: "Item added"
description: "Hook, der ausgelöst wird, wenn ein Item zu einem Inventar hinzugefügt wird."
icon: "circle-plus"
---

Wird ausgelöst, wenn ein Item zu einem Inventar hinzugefügt wird. Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#register-a-hook) unter dem Event-Namen `onItemAdded`.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string | z.B. `"player:1"` |
| `itemName` | string | z.B. `"bread"` |
| `amount` | number | Hinzugefügte Menge |
| `metadata` | table \| nil | Item-Metadaten, kann nil sein |
| `slotId` | number | Slot, zu dem das Item hinzugefügt wurde |

### Beispiele

<AccordionGroup>
  <Accordion title="Ein Rucksack pro Spieler">
    ```lua
    exports['jaksam_inventory']:registerHook("onItemAdded", function(payload)
        local backpackCount = exports["jaksam_inventory"]:getTotalItemAmount(payload.inventoryId, "backpack")
        if backpackCount >= 1 then
            return false, "You can only have one backpack"
        end
    end, {
        itemNameFilter = {backpack = true},
        inventoryTypeFilter = {player = true}
    })
    ```
  </Accordion>

  <Accordion title="Nach bestimmtem Inventarnamen filtern">
    ```lua
    -- Nur auslösen, wenn Items zum Polizei-Stash hinzugefügt werden
    exports['jaksam_inventory']:registerHook("onItemAdded", function(payload)
        print("Item added to police stash:", payload.itemName)
    end, {
        inventoryFilter = {"stash_police"}
    })
    ```
  </Accordion>
</AccordionGroup>

Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für die `registerHook`-API, verfügbare Filter und das Rückgabewert-Verhalten.
