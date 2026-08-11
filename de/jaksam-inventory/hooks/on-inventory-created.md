---
title: "Inventory created"
description: "Hook, der ausgelöst wird, wenn ein neues Inventar erstellt wird."
icon: "wand-magic-sparkles"
---

Wird ausgelöst, wenn ein neues Inventar erstellt wird. Registriere mit [`registerHook`](/de/jaksam-inventory/hooks#register-a-hook) unter dem Event-Namen `onInventoryCreated`.

### Payload

| Feld | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventoryId` | string | z.B. `"player:1"` |
| `inventoryType` | string | z.B. `"player"`, `"stash"`, `"trunk"` |
| `label` | string | Anzeigename des Inventars |
| `options` | table | Optionen, mit denen das Inventar erstellt wurde |
| `items` | table | Anfangs-Items des Inventars |
| `metadata` | table \| nil | Inventar-Metadaten |

### Beispiele

<AccordionGroup>
  <Accordion title="Starter-Items zu neuen Spieler-Inventaren hinzufügen">
    ```lua
    exports['jaksam_inventory']:registerHook("onInventoryCreated", function(payload)
        exports["jaksam_inventory"]:addItem(payload.inventoryId, "water", 2)
        exports["jaksam_inventory"]:addItem(payload.inventoryId, "bread", 1)
        exports["jaksam_inventory"]:addItem(payload.inventoryId, "phone", 1)
    end, {
        inventoryTypeFilter = {player = true}
    })
    ```
  </Accordion>

  <Accordion title="Mülltonnen mit zufälliger Beute befüllen">
    ```lua
    local lootTable = {"plastic", "cardboard", "cash", "phone", "watch"}

    local function shuffle(tbl)
        for i = #tbl, 2, -1 do
            local j = math.random(i)
            tbl[i], tbl[j] = tbl[j], tbl[i]
        end
        return tbl
    end

    exports['jaksam_inventory']:registerHook("onInventoryCreated", function(payload)
        local shuffled = shuffle(lootTable)
        local rollCount = math.random(0, 3)

        for i = 1, rollCount do
            exports["jaksam_inventory"]:addItem(payload.inventoryId, shuffled[i], 1)
        end
    end, {
        inventoryFilter = {"dumpster"}
    })
    ```
  </Accordion>
</AccordionGroup>

Siehe [Hooks-Übersicht](/de/jaksam-inventory/hooks) für die `registerHook`-API, verfügbare Filter und das Rückgabewert-Verhalten.
