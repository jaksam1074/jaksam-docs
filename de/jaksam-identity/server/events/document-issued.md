---
title: "Dokument ausgestellt"
description: "Server-seitig ausgelöst, nachdem ein echtes Dokument ausgestellt wurde."
icon: "id-card"
---

Dieses Event wird ausgelöst, nachdem ein echtes Dokument ausgestellt wurde: in einem Bürgeramt, als Starter-Dokument, durch esx_dmvschool oder das Rathaus, durch den Admin-Befehl oder den Export [Ausstellen](/de/jaksam-identity/server/register/issue).

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:issued", function(serial, typeId, targetSrc, issuerSrc)

end)
```

```lua Example
AddEventHandler("jksm_identity:issued", function(serial, typeId, targetSrc, issuerSrc)
    if typeId == "weapon" then
        print(("Player %d received firearms permit %s"):format(targetSrc, serial))
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string | Die neue Dokumentnummer |
| `typeId` | string | Der Dokumenttyp, ein Schlüssel von `Config.Documents` |
| `targetSrc` | integer | Server-ID des Spielers, der es bekommen hat |
| `issuerSrc` | integer \| nil | Server-ID des Spielers, der es ausgestellt hat, `0` für die Konsole, **nil**, wenn niemand es ausgestellt hat (Amt, Starter-Dokument) |

<Tip>
  Dieselben Argumente erreichen `Editable.OnIssued` in `editable/server.lua`, falls du deinen Code lieber dort hältst.
</Tip>
