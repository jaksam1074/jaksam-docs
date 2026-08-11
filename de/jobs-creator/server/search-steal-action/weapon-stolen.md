---
title: "Waffe gestohlen"
description: "Wird ausgelöst, nachdem ein Spieler etwas über das Actions-Menü gestohlen hat, nur bei Verwendung der Standard-Player-Search/-Rob, funktioniert nicht, wenn diese ersetzt wurde"
icon: "gun"
---

Wird ausgelöst, nachdem ein Spieler eine Waffe über das Actions-Menü gestohlen hat.

<Note>
  Dies funktioniert nur, wenn du die Standard-Player-Search-/Rob-Action verwendest — es wird nicht ausgelöst, wenn du sie durch ein eigenes Modul ersetzt hast.
</Note>

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:weaponStolen", function(playerId, targetId, weaponName)
end)
```

```lua Beispiel
-- Dieses Beispiel für ESX "löscht" die gestohlenen Waffen (evtl. nützlich für Cops)
RegisterNetEvent("jobs_creator:actions:weaponStolen", function(playerId, targetId, weaponName)
    local xPlayer = ESX.GetPlayerFromId(playerId)
    xPlayer.removeWeapon(weaponName)
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers, der die Waffe gestohlen hat |
| `targetId` | integer | Server-ID des Opfers, das die Waffe verloren hat |
| `weaponName` | string | Waffenname |
