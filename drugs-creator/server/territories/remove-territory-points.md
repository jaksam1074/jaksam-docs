---
title: "Remove territory points"
description: "Remove points from a faction in a territory from an external script."
icon: "arrow-down"
---

Removes points from a faction in a territory from an external script.

```lua Export
exports["drugs_creator"]:removeTerritoryPoints(territory, job, amount)
```

### Parameters

| Name         | Data Type | Description                                                                |
| ------------- | --------- | -------------------------------------------------------------------------------- |
| `territory`    | string    | Territory name, or `"*"` to target all territories                                  |
| `job`          | string    | Job/gang name to remove points from, or `"*"` to target all configured factions       |
| `amount`       | integer   | Number of points to remove (must be > 0)                                                |

## Example

```lua
-- Remove 5 points from "vagos" in "RANCHO"
exports["drugs_creator"]:removeTerritoryPoints("RANCHO", "vagos", 5)
```
