---
title: "Documents and register"
description: "How documents, licence classes, the register and forged cards work in Jaksam Identity, and how to add your own document types."
icon: "id-card"
---

## How it works

<CardGroup cols={2}>
  <Card title="The document is the identity" icon="id-card">
    A lookup returns the identity printed on the document. The script never checks who carries it: a stolen real document works until its owner reports it.
  </Card>

  <Card title="Only the server knows what is real" icon="server">
    Real serials live in the register (`jksm_identity_documents`), forged serials in `jksm_identity_forgeries` with their quality. A real and a forged item carry exactly the same metadata.
  </Card>

  <Card title="Facts, not force" icon="scale-balanced">
    Expiry, suspensions and old photos are shown on the card and in the register check. Nothing is removed, blocked or renewed automatically: what follows is roleplay.
  </Card>

  <Card title="The framework holds the licences" icon="list-check">
    ESX: the esx_license tables (`licenses`, `user_licenses`). QBCore/Qbox: the character metadata `licences`.
  </Card>
</CardGroup>

<Note>
  **Anonymity:** the photo is taken from a local, non-networked clone of the character, with mask, hat and glasses removed. Nobody nearby sees the face, and the photo shows no mask.
</Note>

## Document types

Document types are configured in `Config.Documents` (`config/documents.lua`). There are three kinds:

| Kind | Valid in the register when | Example |
| --- | --- | --- |
| `identity` | the record status is valid | ID card |
| `license` | the record status is valid **and** the licence (or at least one of its classes) is still held | Driver licence (classes A, B, C), firearms permit |
| `badge` | the record status is valid **and** the owner still holds the job | LSPD, LSMD, LSC |

Each entry has these fields:

| Field | Description |
| --- | --- |
| `item` | The inventory item name (the item must exist in your inventory) |
| `kind` | `identity`, `license` or `badge` |
| `license` | (`license` only) the licence type: ESX the `licenses` table, QBCore/Qbox the key in the metadata `licences` |
| `licenses` | (`license` only, instead of `license`) one document for several licence types, each a class |
| `job` | (`badge` only) the job the badge belongs to |
| `validityDays` | Days until the document expires, `nil` for never |
| `layout` | `id` (landscape, default) or `badge` (portrait service ID) |
| `theme` | Card look: header, title, colours. Badges also have `word`, `emblem` (`star`, `shield`, `starOfLife`, `wrench`), `authority` and `authorityName` |

### Licence classes

One document can cover several licence types as classes:

```lua
drive = {
    item = 'driver_license',
    kind = 'license',
    licenses = { drive_bike = 'A', drive = 'B', drive_truck = 'C' },
    label = L('doc_driver'),
    validityDays = 180,
},
```

The card prints the classes held when it was issued. The register check shows the classes held now and names every printed class that was revoked.

### Add your own document

Any licence in your framework can become a document. Add the item to your inventory, then one entry here:

```lua
hunting = { item = 'hunting_license', kind = 'license', license = 'hunting', label = 'Hunting licence', validityDays = 120 },
```

The full walkthrough, with the item for each inventory, the look of the card, the offices and badges, is in [Create a custom document](/jaksam-identity/guides/custom-documents).

### Item metadata

Every document carries the same fields: `serial`, `firstname`, `lastname`, `dob`, `sex`, `issued`, `expires`, `photo`, and `classes` for licence classes. `photo` is only a photo ID: the image lives in the `jksm_identity_photos` table.

## Register statuses

Every real document has a status in the register:

| Status | Meaning |
| --- | --- |
| `valid` | Nothing wrong with it |
| `lost` / `stolen` | Reported by the owner at a citizen office |
| `seized` | Taken by an authority |
| `suspended` | Suspended until a set time, valid again afterwards |
| `replaced` | A newer document of the same type was issued to the owner |
| `revoked` | Revoked for good |

A new document always replaces the old one: the older valid document of that type is marked `replaced`.

## The register check

The register check is what an authority sees. It reports:

- **No record:** the serial is unknown, and whether a person with the printed name exists at all
- **Status:** lost, stolen, seized, suspended, replaced or revoked
- **Expired:** the expiry date has passed
- **Licence missing / class revoked:** the licence, or one of the printed classes, is no longer held
- **Left job:** the badge owner no longer has that job
- **Data mismatch:** the printed name or date of birth differs from the register

It never reveals who made a forgery or its quality. Admins see that with `/documents truth <serial>`.

## Using and showing a document

`Config.UseAction` decides what using a document item does:

| Value | Behaviour |
| --- | --- |
| `auto` | Shows it to the nearest player within `Config.ShowDistance`, looks at it when nobody is there |
| `view` | Always looks at it |
| `show` | Always shows it |
| `menu` | Asks each time |

Documents are shown only to players in the same instance. **Shown from a distance only coarse flaws are visible**, in hand you get the close look.

## Forged documents and flaws

A forged card shows flaws on three levels. How many depends on its quality:

| Level | Examples |
| --- | --- |
| At a glance | Seal offset, wrong font, colour off |
| In hand | Photo blur, misaligned text, missing microprint, flat hologram |
| Under UV | UV feature missing |

The UV level shows while the viewer carries the UV lamp item (`Config.UvItem`, default `uv_lamp`). A good forgery can pass every visual check and only fail in the register.

<Info>
  A document made by a jaksam shop or an admin give is **registered** (real), unless its jaksam `rarity` is listed in `Config.UnregisteredRarities`. Then it becomes an unregistered forgery with the quality `Config.UnregisteredQuality`.
</Info>
