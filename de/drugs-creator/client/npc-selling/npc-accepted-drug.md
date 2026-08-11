---
title: "NPC hat Droge akzeptiert"
description: "Wird client-seitig ausgelöst, nachdem ein NPC eine Droge akzeptiert hat, für eigene Animationen."
icon: "check"
---

Wird ausgelöst, nachdem ein NPC die Droge akzeptiert hat, sodass du deine eigene Animation erstellen kannst.

```lua Event
AddEventHandler("drugs_creator:npc:acceptedDrug", function(targetPedNetworkId)

end)
```

### Parameter

| Name                  | Datentyp        | Beschreibung                                                    |
| ---------------------- | ----------------- | ------------------------------------------------------------------- |
| `targetPedNetworkId`   | ped network ID     | Die Netzwerk-ID des Peds, der den Kauf der Droge akzeptiert hat           |

## Beispiel

```lua
RegisterNetEvent("drugs_creator:framework:ready", function()
    -- Deaktiviert die Standard-Animationen des Scripts für den NPC-Verkauf (sonst gäbe es 2 Animationen)
    exports["drugs_creator"]:disableScriptEvent("drugs_creator:npc:acceptedDrug")
end)

-- Neue Animation für NPCs
RegisterNetEvent("drugs_creator:npc:acceptedDrug", function(targetPedNetworkId)
    local plyPed = PlayerPedId()
    local plyCoords = GetEntityCoords(plyPed)

    local targetPed = NetworkGetEntityFromNetworkId(targetPedNetworkId)
    local targetCoords = GetEntityCoords(targetPed)

    local animDict = "mp_common"
    local animName = "givetake1_b"

    while not HasAnimDictLoaded(animDict) do
        Citizen.Wait(0)
        RequestAnimDict(animDict)
    end

    local distance = #(targetCoords - plyCoords)

    if(distance < 1.5) then
        TaskPlayAnim(targetPed, animDict, animName, 4.0, -4.0, -1, 1, 0.0, false, false, false)

        Citizen.Wait(math.random(200, 500))

        TaskPlayAnim(plyPed, animDict, animName, 4.0, -4.0, -1, 1, 0.0, false, false, false)
    else
        local plyHeading = GetEntityHeading(plyPed)
        local netScene = CreateSynchronizedScene(plyCoords - vector3(0.0, 0.0, 1.0), vector3(0.0, 0.0, plyHeading), 2)
        local netSceneTarget = CreateSynchronizedScene(plyCoords - vector3(0.0, 0.0, 1.0), vector3(0.0, 0.0, plyHeading - 180.0), 2)

        TaskSynchronizedScene(plyPed, netScene, animDict, animName, 1.0, 1.0, -1, 1, 1.0, 0.0)
        TaskSynchronizedScene(targetPed, netSceneTarget, animDict, animName, 1.0, 1.0, -1, 1, 1.0, 0.0)

        SetSynchronizedSceneLooped(netScene, true)
        SetSynchronizedSceneLooped(netSceneTarget, true)
    end

    Citizen.Wait(config.npcSecondsToSell * 1000)

    ClearPedTasks(targetPed)
    ClearPedTasks(plyPed)
end)
```
