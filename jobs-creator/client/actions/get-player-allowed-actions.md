---
title: "Get player allowed actions"
description: "Retrieve the list of actions the player's current job is allowed to perform."
icon: "list-check"
---

Retrieve the allowed actions from the player's job.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getAllowedActions()
```

```lua Example
local actions = exports["jobs_creator"]:getAllowedActions()
print(ESX.DumpTable(actions))
--[[
    Example output

    {
        ["canHeal"] = false,
        ["canCheckDrivingLicense"] = false,
        ["canCheckWeaponLicense"] = false,
        ["canRevive"] = false,
        ["canCheckIdentity"] = false,
        ["canRepairVehicles"] = false,
        ["canHandcuff"] = true,
        ["enableBilling"] = true,
        ["canLockpickCars"] = false,
        ["canCheckVehicleOwner"] = false,
        ["canWashVehicles"] = false,
    }
]]
```

</CodeGroup>

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `actions` | table | Key-value table where the key is the action and the value is a boolean indicating whether it's allowed or not |