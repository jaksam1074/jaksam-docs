---
title: "Issue"
description: "Issue a real document to a player and put it in their inventory."
icon: "id-card"
---

Issues a real document: writes it to the register, takes the photo, puts the item in the player's inventory and marks the older valid document of the same type as `replaced`.

<CodeGroup>

```lua Export
exports["jksm_identity"]:Issue(playerId, typeId, options)
```

```lua Example
-- A DMV script issuing the driver licence after a passed test
local serial, reason = exports["jksm_identity"]:Issue(playerId, "drive", {
    issuerSrc = instructorId,
    grant = { "drive" },
})

if serial then
    print("Issued driver licence " .. serial)
else
    print("Not issued: " .. reason)
end
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Server ID of the player who receives the document |
| `typeId` | string | The document type, a key of `Config.Documents` (for example `id_card`, `drive`, `weapon`, `badge_pd`) |
| `options` | table (optional) | See below |

### Options

| Name | Data Type | Description |
| --- | --- | --- |
| `issuerSrc` | integer | Server ID of the player who issues it. `Editable.CanIssue` is asked first, and the issuer is written to the register. `0` means the console |
| `grant` | table | Licence types to give the character before issuing, for example `{ "drive", "drive_truck" }`. Must be licences of this document |
| `force` | boolean | Issue even if the licence (`license` documents) or the job (`badge` documents) is missing |
| `photo` | boolean | `false` to issue without taking a photo |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string \| nil | The new document number, or **nil** if it was not issued |
| `reason` | string \| nil | Why it was not issued: `unknown_type`, `no_player`, `not_allowed`, `license_missing`, `wrong_job`, `busy` (a photo for this player is being taken), `additem_<code>` (the inventory refused the item) |

<Note>
  The photo is taken from the player's character, so the call waits for it. Call it from a thread or an event handler, not from code that must return at once.
</Note>
