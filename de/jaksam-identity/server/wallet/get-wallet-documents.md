---
title: "Wallet-Dokumente abrufen"
description: "Die Dokumente abrufen, die ein Spieler trägt, als Kartendaten für eine Handy-Wallet."
icon: "wallet"
---

Liefert die Dokumente, die der Spieler tatsächlich bei sich hat: zuerst das Hauptinventar, dann die Container in `Config.WalletContainers`. Ein gefälschtes oder gestohlenes Dokument zeigt, was darauf gedruckt ist: Das Register wird nie gefragt.

<CodeGroup>

```lua Export
exports["jksm_identity"]:GetWalletDocuments(playerId)
```

```lua Example
lib.callback.register("my_phone:getWallet", function(source)
    local cards = {}
    for _, document in ipairs(exports["jksm_identity"]:GetWalletDocuments(source)) do
        cards[#cards + 1] = {
            serial = document.serial,
            title = document.title,
            name = document.firstname .. " " .. document.lastname,
            color = document.color,
            photo = document.photo,
        }
    end
    return cards
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `playerId` | integer | Server-ID des Spielers |

### Rückgabewert

Eine Liste von Tabellen, eine pro mitgeführtem Dokument:

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string | Die Dokumentnummer |
| `type` | string | Der Dokumenttyp, ein Schlüssel von `Config.Documents` |
| `kind` | string | `identity`, `license` oder `badge` |
| `label` | string | Das Label des Dokuments |
| `title` | string | Der Kartentitel aus dem Theme, zum Beispiel `DRIVER LICENSE` |
| `color`, `accent` | string | Die Theme-Farben (Hex) |
| `firstname`, `lastname`, `dob`, `sex` | string | Die gedruckte Identität |
| `classes` | string | Die gedruckten Lizenzklassen |
| `rank` | string | Nur Dienstausweise: der gedruckte Rang |
| `issued`, `expires` | string | Die gedruckten Daten |
| `issuedAt`, `expiresAt` | integer \| nil | Die gedruckten Daten als Unix-Zeiten |
| `valid` | boolean | Ob das gedruckte Ablaufdatum noch nicht überschritten ist. Das sagt die Karte, nie das Register |
| `photo` | string \| nil | Das Foto als Data-URL, **nil** bei einem Dokument ohne Foto |
