---
title: "Status changed"
description: "Triggered server side after the register status of a real document changes."
icon: "tag"
---

This event is triggered after the register status of a real document changes, for example when it is reported stolen at an office or suspended through the [Set status](/jaksam-identity/server/register/set-status) export.

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string | The document number |
| `status` | string | The new status: `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` or `revoked` |
| `previous` | string | The status before |
