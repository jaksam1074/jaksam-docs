---
title: "Erlaubte Actions des Spielers abrufen"
description: "Rufe die Liste der Actions ab, die der aktuelle Job des Spielers ausführen darf."
icon: "list-check"
---

Ruft die erlaubten Actions des Jobs des Spielers ab.

<CodeGroup>

```lua Export
exports["jobs_creator"]:getAllowedActions()
```

```lua Beispiel
local actions = exports["jobs_creator"]:getAllowedActions()
print(ESX.DumpTable(actions))
--[[
    Beispielausgabe

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

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `actions` | table | Key-Value-Tabelle, bei der der Key die Action ist und der Wert ein Boolean, der angibt, ob sie erlaubt ist oder nicht |
