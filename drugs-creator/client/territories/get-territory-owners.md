---
title: "Get territory owners"
description: "Get the current owner of each territory."
icon: "flag"
---

Returns a table containing the current owner of each territory.

```lua Export
local owners = exports["drugs_creator"]:getTerritoryOwners()
```

### Returns

| Data Type | Description                                                                    |
| --------- | ----------------------------------------------------------------------------------- |
| table     | A table where key = territory name and value = owning job/gang name, or `nil`         |

## Example

```lua
local owners = exports["drugs_creator"]:getTerritoryOwners()

for territoryName, ownerFaction in pairs(owners) do
    print(territoryName .. " is owned by " .. (ownerFaction or "nobody"))
end
```
