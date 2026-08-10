---
title: "Get all armory weapons"
description: "Retrieve the list of all weapons stored in a specific armory."
icon: "gun"
---

Get a list of all weapons stored in a specific armory ID.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getAllArmoryWeapons(markerId)
```

```lua Example
local markerId = 52
local allWeapons = exports["jobs_creator"]:getAllArmoryWeapons(markerId)
print("All players' weapons in that armory")
print(ESX.DumpTable(allWeapons))
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `markerId` | integer | The marker ID |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `armoryWeapons` | table | List of all weapons contained in the marker |