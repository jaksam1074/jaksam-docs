---
title: "Externe Deferrals"
description: "Die Warteschlange von Easy Allowlist mit einem Framework integrieren, das bereits eigene Connection-Deferrals nutzt, wie QBCores connectqueue."
icon: "code-merge"
---

### Beispiel für QB-Core

**Alter Code**

```lua
-- Path: qb-core/server/events.lua

local function OnPlayerConnecting(name, setKickReason, deferrals)
    local player = source
    local license
    local identifiers = GetPlayerIdentifiers(player)
    deferrals.defer()

    -- Wartezeit erforderlich!
    Wait(0)

    deferrals.update(string.format('Hello %s. Validating Your Rockstar License', name))

    for _, v in pairs(identifiers) do
        if string.find(v, 'license') then
            license = v
            break
        end
    end

    -- Wartezeit erforderlich!
    Wait(2500)

    deferrals.update(string.format('Hello %s. We are checking if you are banned.', name))

    local isBanned, Reason = QBCore.Functions.IsPlayerBanned(player)
    local isLicenseAlreadyInUse = QBCore.Functions.IsLicenseInUse(license)

    Wait(2500)

    deferrals.update(string.format('Welcome %s to {Server Name}.', name))

    if not license then
        deferrals.done('No Valid Rockstar License Found')
    elseif isBanned then
        deferrals.done(Reason)
    elseif isLicenseAlreadyInUse then
        deferrals.done('Duplicate Rockstar License Found')
    else
        deferrals.done()
        Wait(1000)
        TriggerEvent('connectqueue:playerConnect', name, setKickReason, deferrals)
    end
end
```

**Neuer Code**

```lua
-- Path: qb-core/server/events.lua

local function OnPlayerConnecting(name, setKickReason, deferrals)
    local player = source
    local license
    local identifiers = GetPlayerIdentifiers(player)
    deferrals.defer()

    -- Wartezeit erforderlich!
    Wait(0)

    deferrals.update(string.format('Hello %s. Validating Your Rockstar License', name))

    for _, v in pairs(identifiers) do
        if string.find(v, 'license') then
            license = v
            break
        end
    end

    -- Wartezeit erforderlich!
    Wait(2500)

    deferrals.update(string.format('Hello %s. We are checking if you are banned.', name))

    local isBanned, Reason = QBCore.Functions.IsPlayerBanned(player)
    local isLicenseAlreadyInUse = QBCore.Functions.IsLicenseInUse(license)

    Wait(2500)

    deferrals.update(string.format('Welcome %s to {Server Name}.', name))

    if not license then
        deferrals.done('No Valid Rockstar License Found')
    elseif isBanned then
        deferrals.done(Reason)
    elseif isLicenseAlreadyInUse then
        deferrals.done('Duplicate Rockstar License Found')
    else
        --[[
            Wait(1000)
            TriggerEvent('connectqueue:playerConnect', name, setKickReason, deferrals)
        ]]

        deferrals.done()
    end
end
```

### Standard-QB-Core-Warteschlange deaktivieren

Um die Standard-QB-Core-Warteschlange zu deaktivieren, lösche den `connectqueue`-Script-Ordner und entferne die Abhängigkeit im qb-core-Script.

**Beispielpfad: `qb-core/fxmanifest.lua`**

```lua
-- ALTER CODE
dependencies {
	'oxmysql',
	'progressbar',
	'connectqueue'
}
```

```lua
-- NEUER CODE
dependencies {
	'oxmysql',
	'progressbar'
}
```
