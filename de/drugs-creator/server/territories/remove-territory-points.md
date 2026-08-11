---
title: "Territoriums-Punkte entfernen"
description: "Entfernt die Punkte einer Fraktion in einem Territorium aus einem externen Script."
icon: "arrow-down"
---

Entfernt die Punkte einer Fraktion in einem Territorium aus einem externen Script.

```lua Export
exports["drugs_creator"]:removeTerritoryPoints(territory, job, amount)
```

### Parameter

| Name         | Datentyp | Beschreibung                                                                |
| ------------- | --------- | -------------------------------------------------------------------------------- |
| `territory`    | string    | Territoriumsname, oder `"*"`, um alle Territorien anzusprechen                                  |
| `job`          | string    | Job-/Gang-Name, dem Punkte entfernt werden sollen, oder `"*"`, um alle konfigurierten Fraktionen anzusprechen       |
| `amount`       | integer   | Anzahl der zu entfernenden Punkte (muss > 0 sein)                                                |

## Beispiel

```lua
-- Entfernt "vagos" 5 Punkte in "RANCHO"
exports["drugs_creator"]:removeTerritoryPoints("RANCHO", "vagos", 5)
```
