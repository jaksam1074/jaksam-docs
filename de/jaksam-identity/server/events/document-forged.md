---
title: "Dokument gefälscht"
description: "Server-seitig ausgelöst, nachdem eine Fälschung gemacht wurde."
icon: "print"
---

Dieses Event wird ausgelöst, nachdem eine Fälschung gemacht wurde, von einem Spieler, einem NPC-Arbeiter oder durch den Admin-Befehl.

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:forged", function(serial, typeId, quality, forgerId)

end)
```

```lua Example
AddEventHandler("jksm_identity:forged", function(serial, typeId, quality, forgerId)
    if quality >= 90 then
        print(("A near perfect %s was forged (%s)"):format(typeId, serial))
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string | Die Nummer der Fälschung |
| `typeId` | string | Der Dokumenttyp, ein Schlüssel von `Config.Documents` |
| `quality` | integer | Die Qualität, von 0 bis 100 |
| `forgerId` | string \| nil | Der Charakter-Identifier des Fälschers, `'console'` oder **nil** |

<Tip>
  Dieselben Argumente erreichen `Editable.OnForged` in `editable/server.lua`, falls du deinen Code lieber dort hältst.
</Tip>
