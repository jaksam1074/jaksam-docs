---
title: "Create inventory"
description: "Erstellt ein neues Inventar in Datenbank und/oder Speicher (abhängig von den Optionen)."
icon: "square-plus"
---

Erstellt ein neues Inventar in Datenbank und Speicher (abhängig von den Optionen). Existiert bereits ein Inventar mit der gleichen ID, wird das bestehende unverändert zurückgegeben.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:createInventory(id, label, options, items, inventoryType, metadata)
```

```lua Example
-- Beispiel: Eine Loot-Kiste mit dynamischem Loot basierend auf der Seltenheit erstellen
-- Vergiss nicht, das Event je nach Anwendungsfall irgendwie abzusichern, sonst können Cheater es einfach auslösen, um kostenlosen Loot zu bekommen
RegisterNetEvent('myresource:openLootCrate', function(rarity)
    local playerId = source

    -- Loot-Pools basierend auf der Seltenheit definieren
    local lootPools = {
        common = {
            minTypes = 1,
            maxTypes = 2,
            items = {
                { name = "water",   chance = 15, min = 1, max = 3 },
                { name = "bread",   chance = 15, min = 1, max = 2 },
                { name = "bandage", chance = 10, min = 1, max = 2 },
            }
        },
        rare = {
            minTypes = 2,
            maxTypes = 4,
            items = {
                { name = "water",         chance = 10, min = 2, max = 4 },
                { name = "bread",         chance = 8,  min = 2, max = 3 },
                { name = "bandage",       chance = 8,  min = 2, max = 3 },
                { name = "lockpick",      chance = 5,  min = 1, max = 2 },
                { name = "weapon_pistol", chance = 2,  min = 1, max = 1 },
            }
        },
        legendary = {
            minTypes = 3,
            maxTypes = 5,
            items = {
                { name = "water",         chance = 8,  min = 3, max = 5 },
                { name = "bandage",       chance = 8,  min = 3, max = 4 },
                { name = "lockpick",      chance = 6,  min = 2, max = 3 },
                { name = "weapon_pistol", chance = 4,  min = 1, max = 1 },
                { name = "weapon_rifle",  chance = 2,  min = 1, max = 1 },
            }
        }
    }

    local selectedLoot = lootPools[rarity] or lootPools.common

    local inventory = exports['jaksam_inventory']:createInventory(
        nil, -- ID automatisch generieren
        "Loot Crate (" .. rarity .. ")", -- Dynamisches Label
        {
            temporary = true, -- Inventar geht beim Script-Neustart verloren
            maxSlots = 5,
            maxWeight = 50.0,
            disableIncoming = true, -- Items können vom Spieler nicht zu diesem Inventar hinzugefügt werden
            prefillItems = selectedLoot,
            revealItems = {
                delayPerItem = 1000,
                randomOrder = true
            }
        },
        nil,
        'stash',
        nil
    )

    -- Das Inventar-Interface für den Spieler öffnen
    if inventory then
        exports['jaksam_inventory']:forceOpenInventory(playerId, inventory.id)
    end
end)
```

```lua Example: persistenter Stash
-- Einen persistenten Stash mit festen Startitems erstellen
local inventory = exports['jaksam_inventory']:createInventory(
    "welcome_kit_" .. charId,
    "Welcome Kit",
    { maxSlots = 5, maxWeight = 20.0 },
    {
        {"bread", 3, nil},
        {"water", 2, nil},
    },
    'stash',
    nil
)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `id` | string \| nil | Eindeutige Kennung für das Inventar. Bei nil wird eine zufällige ID generiert |
| `label` | string \| nil | Anzeigename für das Inventar. Bei nil wird eine Übersetzung basierend auf dem Inventartyp verwendet |
| `options` | table | Konfigurationsoptionen für das Inventar (siehe Hinweise unten) |
| `items` | table | Statische Items, die beim ersten Erstellen des Inventars hinzugefügt werden. Array-Format: `{{itemName, amount, metadata}, ...}`. Wird ignoriert, falls das Inventar bereits in der Datenbank existiert |
| `inventoryType` | string | Typ des Inventars. Standard: "stash". Weitere Werte: "player", "trunk", "glovebox" |
| `metadata` | table | Zusätzliche Metadaten für das Inventar |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `inventory` | table \| nil | Die erstellte (oder bestehende) Inventar-Tabelle, oder nil falls die Erstellung fehlgeschlagen ist. Struktur: `{id, label, options, items, type, totalWeight, metadata}` |

### Hinweise

`options`-Felder:

- `maxWeight` (number, optional): Maximale Gewichtskapazität
- `maxSlots` (number, optional): Maximale Anzahl an Slots
- `columns` (number, optional): Anzahl der Spalten für die Grid-Darstellung in der UI (z.B. 10 Slots insgesamt, aber 2 Spalten → 2x5-Grid)
- `temporary` (boolean, optional): Bei true wird das Inventar nicht in der Datenbank gespeichert und geht beim Script-Neustart verloren
- `prefillItems` (table, optional): Konfiguration für zufälligen Loot. Items werden per gewichteter Auswahl ohne Zurücklegen ausgewählt:
  - `minTypes` (number, optional): Minimale Anzahl unterschiedlicher Item-Typen. Standard: 1
  - `maxTypes` (number, optional): Maximale Anzahl unterschiedlicher Item-Typen. Standard: Pool-Größe
  - `items` (table, erforderlich): Array möglicher Items, jeder Eintrag: `{name = string, chance = number, min = number, max = number, metadata = table?}`
- `revealItems` (table, optional): Schrittweise Item-Enthüllungsanimation beim Öffnen des Inventars:
  - `delayPerItem` (number, optional): Millisekunden zwischen jeder Item-Enthüllung. Standard: 1000
  - `randomOrder` (boolean, optional): Bei true werden Items in zufälliger statt Slot-Reihenfolge enthüllt. Standard: false
- `slots` (table, optional): Konfiguration pro Slot. Key ist die Slot-Nummer, Wert ist eine `SlotConfig`-Tabelle: `label`, `image`, `opacity`, `whitelist`, `blacklist`
- `whitelist` / `blacklist` (table, optional): Item-Filter auf Inventarebene. Format: `{itemName = true, ...}`
- `allowedJobs` (table, optional): Jobs, die auf dieses Inventar zugreifen dürfen
- `allowedIdentifiers` (table, optional): Charakter-Identifier, die auf dieses Inventar zugreifen dürfen
- `disableIncoming` / `disableOutgoing` (boolean, optional): Transfers vom/zum Spieler blockieren
- `dropDisabled` (boolean, optional): Bei true können Items aus diesem Inventar nicht fallen gelassen werden
- `noLimitDrag` (boolean, optional): Bei true überspringt das Ziehen den Mengenauswahl-Dialog und bewegt den ganzen Stack. Intern für Shops genutzt

Außerdem:

- Existiert `id` bereits, wird das bestehende Inventar unverändert zurückgegeben, statische `items` und `prefillItems` werden NICHT erneut angewendet
- `prefillItems` nutzt gewichtete Zufallsauswahl ohne Zurücklegen (jeder Item-Typ kann nur einmal ausgewählt werden)
- `prefillItems` wird über `options` verarbeitet, während statische `items` ein separater Parameter sind, sie dienen unterschiedlichen Zwecken
- Nutze `temporary = true` für kurzlebige Inventare (Lootboxen, Event-Belohnungen), um Datenbank-Aufblähung zu vermeiden
