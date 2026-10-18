---
title: "Status geändert"
description: "Server-seitig ausgelöst, nachdem sich der Register-Status eines echten Dokuments geändert hat."
icon: "tag"
---

Dieses Event wird ausgelöst, nachdem sich der Register-Status eines echten Dokuments geändert hat, zum Beispiel wenn es in einem Amt als gestohlen gemeldet oder über den Export [Status setzen](/de/jaksam-identity/server/register/set-status) gesperrt wird.

<CodeGroup>

```lua Event
AddEventHandler("jksm_identity:statusChanged", function(serial, status, previous)

end)
```

```lua Example
AddEventHandler("jksm_identity:statusChanged", function(serial, status, previous)
    if status == "stolen" then
        -- flag it in your MDT
        exports["my_mdt"]:AddFlag(serial, "Reported stolen")
    end
end)
```

</CodeGroup>

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `serial` | string | Die Dokumentnummer |
| `status` | string | Der neue Status: `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` oder `revoked` |
| `previous` | string | Der Status davor |
