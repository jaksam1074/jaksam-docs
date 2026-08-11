---
title: "Register item"
description: "Registriert zur Laufzeit eine neue Item-Definition (nur im Speicher, nicht in einer Datei gespeichert)."
icon: "cube"
---

Registriert zur Laufzeit eine neue Item-Definition (nur im Speicher, nicht in einer Datei gespeichert). Es werden nur sichere, deklarative Felder akzeptiert, alles andere wird auf jeder Ebene verworfen.

<Note>
  Auf diese Weise registrierte Items gehen beim Neustart der Resource verloren. Nutze das, um externen Scripts zu erlauben, eigene Items zu definieren, ohne `_data/items.lua` zu bearbeiten.
</Note>

<CodeGroup>

```lua Export
exports['jaksam_inventory']:registerItem(itemName, itemData)
```

```lua Example: Verbrauchsgegenstand
-- Ein einfaches Verbrauchsitem registrieren
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

```lua Example: Waffe
-- Ein Waffen-Item registrieren
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

```lua Example: Behälter
-- Ein Behälter-Item registrieren
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

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Eindeutige Item-Kennung (z.B. `'custom_radio'`). Darf noch nicht in der Item-Registry existieren |
| `itemData` | table | Item-Definitionstabelle (siehe Hinweise unten für akzeptierte Felder) |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `success` | boolean | True, falls das Item erfolgreich registriert wurde |
| `errorMessage` | string \| nil | Fehlerbeschreibung, falls die Registrierung fehlgeschlagen ist |

### Hinweise

`itemData` akzeptiert nur die folgenden sicheren Felder; jedes andere Feld wird stillschweigend entfernt:

**Erforderliche Felder:** `label` (string), `weight` (number, >= 0), `stackable` (boolean)

**Optionale Felder:** `description`, `image`, `close`, `maxStack`, `rarity`, `type`, `customSymbol`, `ammo`, `durability`, `degrade`, `decay`, `consume`, `isGrenadeType`, `separateWeight`, `universal`, `oxClientEvent`, `oxClientExport`, `oxServerExport`

**Optionale Table-Felder** (rekursiv validiert, keine Funktionen darin erlaubt): `metadata`, `status`, `useOptions`, `inventoryOptions`, `throwableOptions`, `dynamicMetadata`

Außerdem:

- Mit `registerItem` registrierte Items existieren nur im Speicher. Sie gehen beim Neustart der Resource verloren. Für persistente Items nutze das Ingame-Adminmenü oder trage sie in `_data/items.lua` ein
- Unbekannte Items werden erst beim ersten Laden jedes Inventars bereinigt, nicht beim Start, dein Script kann `registerItem` also jederzeit sicher aufrufen, bevor auf das Spielerinventar zugegriffen wird, typischerweise beim Resource-Start
- Du kannst `registerItem` mit `registerUsableItem` kombinieren, um sowohl das Item als auch sein Nutzungsverhalten aus einem externen Script zu definieren
- Existiert der Item-Name bereits, wird die Registrierung abgelehnt, um dateidefinierte Items nicht zu überschreiben
- Table-Felder (wie `metadata`, `useOptions` usw.) werden tief kopiert, Änderungen an der Originaltabelle nach der Registrierung haben also keine Auswirkung
