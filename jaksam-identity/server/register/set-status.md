---
title: "Set status"
description: "Change the register status of a real document: lost, stolen, seized, suspended, replaced, revoked or valid."
icon: "tag"
---

Sets the register status of a real document. The change is logged and triggers the [status changed](/jaksam-identity/server/events/status-changed) event.

<CodeGroup>

```lua Export
exports["jksm_identity"]:SetStatus(serial, status, options)
```

```lua Example
-- Suspend a driver licence for 7 days from an MDT
local ok, reason = exports["jksm_identity"]:SetStatus("SAAB1234567", "suspended", {
    untilTime = os.time() + 7 * 24 * 60 * 60,
    note = "Speeding, 7 days",
    actor = officerIdentifier,
})

if not ok then print("Failed: " .. reason) end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string | The document number |
| `status` | string | `valid`, `lost`, `stolen`, `seized`, `suspended`, `replaced` or `revoked` |
| `options` | table (optional) | See below |

### Options

| Name | Data Type | Description |
| --- | --- | --- |
| `untilTime` | integer | Only with `suspended`: unix time when the suspension ends. Afterwards the register check returns `valid` again |
| `note` | string | A note stored with the status (up to 255 characters) |
| `actor` | string | Who changed it, written to the admin log |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `ok` | boolean | **true** if the status was changed |
| `reason` | string \| nil | `bad_arguments` or `not_found` (the serial is not a real document) |
