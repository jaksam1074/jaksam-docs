---
title: "Post use item"
description: "Hook, der nach der Nutzung eines Items ausgelöst wird, nur zur Benachrichtigung."
icon: "circle-check"
---

Wird NACH der Nutzung eines Items ausgelöst (nach Verbrauch, Animationen, Verzögerungen und allen Callbacks). Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#register-a-hook) unter dem Event-Namen `onPostUseItem`.

**Ausführungsreihenfolge:** ganz am Ende des Item-Nutzungsprozesses, nach `oxServerExport 'usedItem'`.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | number | Der Spieler, der das Item benutzt hat |
| `inventoryId` | string | z.B. `"license:abcd1234"` |
| `slotId` | number | Slot des benutzten Items |
| `itemName` | string | z.B. `"bread"` |
| `metadata` | table \| nil | Item-Metadaten |

<Note>
  Dieser Hook dient nur zur Benachrichtigung und kann die Item-Nutzung nicht abbrechen. Nützlich für Logging, Statistiken, Erfolge und das Auslösen externer Systeme.
</Note>

### Beispiele

<AccordionGroup>
  <Accordion title="Alle Item-Nutzungen loggen">
    ```lua
    exports['jaksam_inventory']:registerHook("onPostUseItem", function(payload)
        print(("Player %d used %s"):format(payload.playerId, payload.itemName))
        -- An externes Logging-System, Datenbank usw. senden
    end)
    ```
  </Accordion>

  <Accordion title="Essensverbrauch-Statistiken erfassen">
    ```lua
    local foodStats = {}

    exports['jaksam_inventory']:registerHook("onPostUseItem", function(payload)
        foodStats[payload.itemName] = (foodStats[payload.itemName] or 0) + 1
        print("Total", payload.itemName, "consumed:", foodStats[payload.itemName])
    end, {
        itemTypeFilter = {food = true}
    })
    ```
  </Accordion>
</AccordionGroup>

Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für die `registerHook`-API, verfügbare Filter und das Rückgabewert-Verhalten.
