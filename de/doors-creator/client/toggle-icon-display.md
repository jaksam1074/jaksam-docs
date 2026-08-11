---
title: "Symbolanzeige umschalten"
description: "Zeige oder verstecke die Symbole/Texte aller Türen."
icon: "eye"
---

Schaltet die Symbole/Texte aller Türen um.

```lua Export
exports["doors_creator"]:toggleIconDisplay(newState)
```

### Parameter

| Name       | Datentyp | Beschreibung                                          |
| ---------- | --------- | ----------------------------------------------------- |
| `newState` | boolean   | `true` = Symbol/Text anzeigen, `false` = Symbol/Text verstecken   |

## Beispiel

```lua
RegisterCommand("hideDoorsIcon", function()
    exports["doors_creator"]:toggleIconDisplay(false)
end)
```
