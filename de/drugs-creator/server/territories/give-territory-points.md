---
title: "Territoriums-Punkte geben"
description: "Fügt einer Fraktion in einem Territorium Punkte aus einem externen Script hinzu."
icon: "arrow-up"
---

Fügt einer Fraktion in einem Territorium Punkte aus einem externen Script hinzu.

```lua Export
exports["drugs_creator"]:giveTerritoryPoints(territory, job, amount)
```

### Parameter

| Name         | Datentyp | Beschreibung                                                             |
| ------------- | --------- | ---------------------------------------------------------------------------- |
| `territory`    | string    | Territoriumsname, oder `"*"`, um alle Territorien anzusprechen                              |
| `job`          | string    | Job-/Gang-Name, dem Punkte gegeben werden sollen, oder `"*"`, um alle konfigurierten Fraktionen anzusprechen       |
| `amount`       | integer   | Anzahl der hinzuzufügenden Punkte (muss > 0 sein)                                              |

## Beispiel

```lua
-- Gibt "ballas" 2 Punkte in "RANCHO"
exports["drugs_creator"]:giveTerritoryPoints("RANCHO", "ballas", 2)

-- Gibt allen Fraktionen in allen Territorien 3 Punkte
exports["drugs_creator"]:giveTerritoryPoints("*", "*", 3)
```
