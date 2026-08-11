---
title: "Territoriums-Punkte zurücksetzen"
description: "Setzt die Punkte einer Fraktion in einem Territorium auf 0 zurück."
icon: "rotate-left"
---

Setzt die Punkte einer Fraktion in einem Territorium zurück (auf 0). Der Besitz wird nach dem Zurücksetzen neu berechnet.

```lua Export
exports["drugs_creator"]:resetTerritoryPoints(territory, job)
```

### Parameter

| Name         | Datentyp | Beschreibung                                                          |
| ------------- | --------- | -------------------------------------------------------------------------- |
| `territory`    | string    | Territoriumsname, oder `"*"`, um alle Territorien anzusprechen                            |
| `job`          | string    | Job-/Gang-Name, der zurückgesetzt werden soll, oder `"*"`, um alle konfigurierten Fraktionen anzusprechen              |

## Beispiel

```lua
-- Setzt die Punkte von "ballas" in "RANCHO" zurück
exports["drugs_creator"]:resetTerritoryPoints("RANCHO", "ballas")

-- Vollständiges Zurücksetzen: alle Fraktionen in allen Territorien
exports["drugs_creator"]:resetTerritoryPoints("*", "*")
```
