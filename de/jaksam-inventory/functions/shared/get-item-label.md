---
title: "Get item label"
description: "Ruft nur das Label (den Anzeigenamen) eines Items ab. Eine einfachere und schnellere Alternative zu getStaticItem, wenn nur das Label benötigt wird."
icon: "tag"
---

Ruft nur das Label (den Anzeigenamen) eines Items ab. Das ist eine einfachere und schnellere Alternative zu `getStaticItem`, wenn du nur das Label des Items brauchst.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemLabel(itemName)
```

```lua Example
local label = exports['jaksam_inventory']:getItemLabel('bread')
print(label) -- Bread

-- Nicht gefundenes Item gibt nil zurück
local notFound = exports['jaksam_inventory']:getItemLabel('invalid_item')
print(notFound) -- nil
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `itemName` | string | Der Name des Items, dessen Label abgerufen werden soll |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `label` | string \| nil | Das Label (der Anzeigename) des Items, oder nil, falls das Item nicht gefunden wurde |
