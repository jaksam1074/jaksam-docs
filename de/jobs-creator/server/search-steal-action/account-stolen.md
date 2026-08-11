---
title: "Geld gestohlen"
description: "Wird ausgelöst, nachdem ein Spieler über das Actions-Menü Geld gestohlen hat, nur bei Verwendung der Standard-Search-/Rob-Action."
icon: "money-bill-transfer"
---

Wird ausgelöst, nachdem ein Spieler über das Actions-Menü Geld gestohlen hat.

<Note>
  Dies funktioniert nur, wenn du die Standard-Player-Search-/Rob-Action verwendest — es wird nicht ausgelöst, wenn du sie durch ein eigenes Modul ersetzt hast.
</Note>

<CodeGroup>

```lua Event
RegisterNetEvent("jobs_creator:actions:accountStolen", function(playerId, targetId, accountName, amount)
end)
```

```lua Beispiel
RegisterNetEvent("jobs_creator:actions:accountStolen", function(playerId, targetId, accountName, amount)
    print(GetPlayerName(playerId) .. " hat " .. amount .. " " .. accountName .. " von " .. GetPlayerName(targetId) .. " gestohlen")
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers, der das Geld gestohlen hat |
| `targetId` | integer | Server-ID des Opfers, das das Geld verloren hat |
| `accountName` | string | Kontoname (Beispiel: "bank") |
| `amount` | integer | Gestohlener Betrag |
