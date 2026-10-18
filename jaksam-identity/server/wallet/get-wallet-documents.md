---
title: "Get wallet documents"
description: "Get the documents a player carries, as card data for a phone wallet."
icon: "wallet"
---

Returns the documents the player physically carries: the main inventory first, then the containers listed in `Config.WalletContainers`. A forged or stolen document shows what is printed on it: the register is never asked.

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `playerId` | integer | Server ID of the player |

### Return value

A list of tables, one per carried document:

| Name | Data Type | Description |
| --- | --- | --- |
| `serial` | string | The document number |
| `type` | string | The document type, a key of `Config.Documents` |
| `kind` | string | `identity`, `license` or `badge` |
| `label` | string | The document label |
| `title` | string | The card title from the theme, for example `DRIVER LICENSE` |
| `color`, `accent` | string | The theme colours (hex) |
| `firstname`, `lastname`, `dob`, `sex` | string | The printed identity |
| `classes` | string | The printed licence classes |
| `rank` | string | Badges only: the printed rank |
| `issued`, `expires` | string | The printed dates |
| `issuedAt`, `expiresAt` | integer \| nil | The printed dates as unix times |
| `valid` | boolean | Whether the printed expiry date has not passed. It's what the card says, never the register |
| `photo` | string \| nil | The photo as a data URL, **nil** for a document without photo |
