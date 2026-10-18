---
title: "Document issued"
description: "Triggered server side after a real document is issued."
icon: "id-card"
---

This event is triggered after a real document is issued: at a citizen office, as a starter document, by esx_dmvschool or the city hall, by the admin command or by the [Issue](/jaksam-identity/server/register/issue) export.

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string | The new document number |
| `typeId` | string | The document type, a key of `Config.Documents` |
| `targetSrc` | integer | Server ID of the player who received it |
| `issuerSrc` | integer \| nil | Server ID of the player who issued it, `0` for the console, **nil** when nobody issued it (office, starter document) |

<Tip>
  The same arguments reach `Editable.OnIssued` in `editable/server.lua`, if you prefer to keep your code there.
</Tip>
