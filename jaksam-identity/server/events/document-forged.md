---
title: "Document forged"
description: "Triggered server side after a forgery is made."
icon: "print"
---

This event is triggered after a forgery is made, by a player, an NPC worker or the admin command.

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string | The number of the forgery |
| `typeId` | string | The document type, a key of `Config.Documents` |
| `quality` | integer | The quality, from 0 to 100 |
| `forgerId` | string \| nil | The character identifier of the forger, `'console'`, or **nil** |

<Tip>
  The same arguments reach `Editable.OnForged` in `editable/server.lua`, if you prefer to keep your code there.
</Tip>
