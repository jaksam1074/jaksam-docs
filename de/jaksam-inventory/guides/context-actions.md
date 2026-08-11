---
title: "Context Actions"
icon: "hand-pointer"
description: "Eigene Rechtsklick-Buttons zu Items hinzufügen, entweder einzeln oder nach Item-Typ"
---

Context Actions sind eigene Buttons, die erscheinen, wenn du mit Rechtsklick auf ein Item in deinem Inventar klickst. Damit können Spieler bestimmte Aktionen mit Items ausführen, wie Benutzen, Untersuchen oder jedes beliebige eigene Verhalten.

<Columns cols={2}>
  <Frame>
    ![Item context actions screenshot](/images/context-actions-screenshot.png)
  </Frame>

  <Frame>
    ![Item context actions code screenshot](/images/context-actions-code.png)
  </Frame>
</Columns>

## Wann welche Methode nutzen

<CardGroup cols={2}>
  <Card title="Einzelnes Item" icon="circle-dot">
    Nutzen, wenn du Buttons für EIN bestimmtes Item willst (z.B. nur beim "water"-Item)
  </Card>

  <Card title="Nach Typ" icon="layer-group">
    Nutzen, wenn du die gleichen Buttons bei ALLEN Items des gleichen Typs willst (z.B. alle Waffen, alle Behälter)
  </Card>
</CardGroup>

## Methode 1: Buttons zu einem einzelnen Item hinzufügen

Um eigene Buttons zu einem bestimmten Item hinzuzufügen, öffne `jaksam_inventory/_data/items.lua` und finde oder erstelle dein Item. Füge die `contextActions`-Eigenschaft hinzu:

```lua
['water'] = {
    label = 'Water',
    weight = 1.0,
    stackable = true,
    close = true,
    description = 'A bottle of water',
    maxStack = 10,
    contextActions = {
        {
            label = 'Drink',                    -- Button-Text, den Spieler sehen
            icon = 'bi-droplet',                -- Icon (Bootstrap Icons)
            callback = function(inventoryId, slotIndex)
                -- Dein Code hier, läuft wenn der Button geklickt wird
                TriggerServerEvent('myserver:drinkWater', inventoryId, slotIndex)
            end
        },
        {
            label = 'Check expiration',
            icon = 'bi-calendar-check',
            callback = function(inventoryId, slotIndex)
                print('Checking expiration date...')
                -- Füge hier deine Logik hinzu
            end
        }
    }
},
```

<Note>
  **Wichtige Hinweise:**

  - `inventoryId`: Gibt an, in welchem Inventar sich das Item befindet (Spieler-Inventar, Kofferraum, usw.)
  - `slotIndex`: Die Slot-Nummer, in der sich das Item befindet
  - `icon`: Nutze Bootstrap Icons (suche online nach "bootstrap icons" für Icon-Namen)
</Note>

## Methode 2: Buttons zu allen Items eines bestimmten Typs hinzufügen

Falls du die gleichen Buttons bei ALLEN Items des gleichen Typs willst (wie alle Waffen, alle Lebensmittel usw.), nutze das Defaults-System.

Öffne `jaksam_inventory/_data/defaults.lua` und füge den gewünschten Typ hinzu oder bearbeite ihn:

```lua
Script.defaultsByType = {
    ['weapon'] = {
        displayFields = {
            -- ... bestehende display fields ...
        },
        contextActions = {
            {
                label = 'Empty ammo',
                icon = 'bi-asterisk',
                callback = function(inventoryId, slotIndex)
                    TriggerServerEvent(Utils.eventsPrefix .. ":emptyAmmo", inventoryId, slotIndex)
                end
            },
            {
                label = 'View components',
                icon = 'bi-eye',
                callback = function(inventoryId, slotIndex)
                    Script.closeInventoryUI()
                    Script.viewComponents(inventoryId, slotIndex)
                end
            }
        }
    },

    ['food'] = {
        contextActions = {
            {
                label = 'Eat',
                icon = 'bi-egg-fried',
                callback = function(inventoryId, slotIndex)
                    TriggerServerEvent('myserver:eatFood', inventoryId, slotIndex)
                end
            }
        }
    },
}
```

Das bedeutet:

- ALLE Items mit `type = 'weapon'` haben die Buttons "Empty ammo" und "View components"
- ALLE Items mit `type = 'food'` haben einen "Eat"-Button

## Globale Buttons zu ALLEN Items hinzufügen

Du kannst auch Buttons hinzufügen, die bei JEDEM Item im Spiel erscheinen, über den speziellen `['*']`-Key:

```lua
Script.defaultsByType = {
    ['*'] = {
        contextActions = {
            {
                label = 'Inspect',
                icon = 'bi-search',
                callback = function(inventoryId, slotIndex)
                    print('Inspecting item...')
                    -- Dein Code hier
                end
            }
        }
    },
}
```
