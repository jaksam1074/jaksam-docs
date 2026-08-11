---
title: "Hooks"
icon: "webhook"
description: "Inventar-Verhalten mit serverseitigen Hooks für Item-Übertragungen, -Nutzung und -Erstellung abfangen und ändern"
tag: "Updated"
---

Hooks sind eine Möglichkeit, das Verhalten des Inventarsystems zu verändern. Sie werden auf dem Server registriert und können z.B. genutzt werden, um Spieler daran zu hindern, Items in ein bestimmtes Inventar zu verschieben. Einige Beispiele für Hooks findest du im Ordner `jaksam_inventory/_hooks`.

## Best Practices

<CardGroup cols={3}>
  <Card title="Filter nutzen" icon="filter">
    Verwende immer passende Filter, um unnötige Hook-Ausführungen zu vermeiden
  </Card>

  <Card title="Frühe Rückgaben" icon="right-from-bracket">
    Nutze frühe `return`s, um Hooks zu verlassen, wenn Bedingungen nicht erfüllt sind
  </Card>

  <Card title="Performance" icon="gauge-high">
    Halte die Hook-Logik schlank, um die Inventar-Performance nicht zu beeinträchtigen
  </Card>
</CardGroup>

## Anwendungsbeispiele

- Verhindern, dass Spieler Items mit dem Metadaten-Feld `sole_owner` stehlen (z.B. VIP-Items)
- Verhindern, dass Spieler Polizeiwaffen in ihr persönliches Inventar verschieben
- Nur einen Rucksack pro Spieler-Inventar erlauben
- Items craften, indem ein bestimmtes Item auf ein anderes gezogen wird (z.B. Brot auf Fleisch ziehen ergibt ein Sandwich)
- Item-Nutzung blockieren, wenn der Spieler gefesselt ist oder sich in bestimmten Zonen befindet
- Item-Nutzungsstatistiken und Erfolge erfassen
- Die Nutzung bestimmter Items in Fahrzeugen verhindern
- Neuen Spieler-Inventaren bei der Erstellung Starter-Items hinzufügen
- Mülltonnen oder Stashes bei der Erstellung mit zufälligen Items vorbefüllen

## API-Funktionen

### Einen Hook registrieren

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerHook(eventName, callback, options, priority)
```

</CodeGroup>

#### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `eventName` | string | Der Name des Hook-Events, auf das gehört werden soll (siehe [Verfügbare Hook-Events](#verfugbare-hook-events) unten) |
| `callback` | function | Die Funktion, die beim Auslösen des Hooks ausgeführt wird |
| `options` | table | Filter und Konfigurationsoptionen (siehe [Options-Parameter](#options-parameter) unten) |
| `priority` | number | Ausführungspriorität (höhere Zahlen werden zuerst ausgeführt, Standard: 0) |

#### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `hookId` | string | Eindeutige ID des registrierten Hooks (wird zum Deregistrieren des Hooks benötigt) |

### Einen Hook deregistrieren

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterHook(hookId)
```

</CodeGroup>

#### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `hookId` | string | Die eindeutige ID, die beim Registrieren des Hooks zurückgegeben wurde |

### Alle Hooks einer Resource deregistrieren

<CodeGroup>

```lua Export
exports['jaksam_inventory']:unregisterResourceHooks(resourceName)
```

</CodeGroup>

#### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `resourceName` | string | Name der Resource, deren Hooks alle deregistriert werden sollen |

## Options-Parameter

Der Options-Parameter akzeptiert eine Table mit Filtern zur Performance-Optimierung.

<Tabs>
  <Tab title="Allgemein (alle Events)">
    ```lua
        local options = {
            -- Debug: Bei Auslösung des Hooks in die Konsole ausgeben
            print = true,

            -- Nur für bestimmte Items auslösen
            itemNameFilter = {
                bread = true,
                weapon_pistol = true
            },

            -- Nur für bestimmte Item-Typen auslösen
            itemTypeFilter = {
                weapon = true,
                currency = true
            }
        }
    ```
  </Tab>
  <Tab title="Inventar-Filter">
    Für `onItemAdded`, `onItemRemoved`, `onInventoryCreated`:

    ```lua
        local options = {
            -- Nach Inventartyp filtern (empfohlen)
            inventoryTypeFilter = {
                player = true,
                stash = true
            },

            -- Nach bestimmten Inventarmustern filtern (fortgeschritten)
            inventoryFilter = {
                "player:.*",      -- Alle Spieler
                "stash_police"    -- Bestimmter Stash
            }
        }
    ```
  </Tab>
  <Tab title="Übertragungs-Filter">
    Nur für `onItemTransferred`:

    ```lua
        local options = {
            -- Quell-Inventar nach Typ filtern
            inventoryFromTypeFilter = { player = true },

            -- Quell-Inventar nach Namensmuster filtern
            inventoryFromFilter = {
                "player:.*",      -- Alle Spieler
                "vehicle:123"     -- Bestimmtes Fahrzeug
            },

            -- Ziel-Inventar nach Typ filtern
            inventoryToTypeFilter = { stash = true },

            -- Ziel-Inventar nach Namensmuster filtern
            inventoryToFilter = {
                "stash_police",   -- Bestimmter Stash
                "container:.*"    -- Alle Container
            },

            -- Nur Bewegungen innerhalb desselben Inventars (Ziehen im gleichen Inventar)
            intraInventoryOnly = true
        }
    ```
  </Tab>
</Tabs>

## Verfügbare Hook-Events

| Event | Beschreibung |
| --- | --- |
| [Item added](/de/jaksam-inventory/hooks/on-item-added) | Wird ausgelöst, wenn ein Item zu einem Inventar hinzugefügt wird |
| [Item removed](/de/jaksam-inventory/hooks/on-item-removed) | Wird ausgelöst, wenn ein Item aus einem Inventar entfernt wird |
| [Item transferred](/de/jaksam-inventory/hooks/on-item-transferred) | Wird ausgelöst, wenn ein Item zwischen Inventaren übertragen wird |
| [Pre use item](/de/jaksam-inventory/hooks/on-pre-use-item) | Wird vor der Nutzung eines Items ausgelöst, kann die Nutzung abbrechen |
| [Post use item](/de/jaksam-inventory/hooks/on-post-use-item) | Wird nach der Nutzung eines Items ausgelöst, nur zur Benachrichtigung |
| [Inventory created](/de/jaksam-inventory/hooks/on-inventory-created) | Wird ausgelöst, wenn ein neues Inventar erstellt wird |

## Hook-Verhalten

<CardGroup cols={2}>
  <Card title="Priorität" icon="arrow-up-1-9">
    Höhere Zahlen werden zuerst ausgeführt (Standard: 0)
  </Card>

  <Card title="Rückgabewerte" icon="reply">
    `return nil` oder `return true`: die Aktion wird fortgesetzt.

    `return false, "message", "notifyType"`: verhindert die Aktion und stoppt die weitere Hook-Ausführung. Die Parameter message und notifyType sind optional (notifyType kann `"error"`, `"success"`, `"info"` sein)
  </Card>
</CardGroup>
