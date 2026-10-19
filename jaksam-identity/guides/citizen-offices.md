---
title: "Citizen offices"
description: "Starter documents, citizen offices with an NPC at the counter, fees, and the esx_dmvschool integration."
icon: "building-columns"
---

## Starter documents

Every character that never had a document of the listed types gets one after loading, as soon as its name and date of birth are set.

```lua
Config.Starter = {
    documents = { 'id_card' },
    delaySeconds = 15,          -- after the character has loaded
}
```

Starter documents have **no photo**: the photo is taken at the office with a renewal. Set `documents = {}` to turn this off.

## Citizen offices

An office is an NPC at a counter, with a blip on the map. Each office handles the document types it lists. Players can:

- **Apply** for a first document
- **Renew** it: same number, new expiry and photo (the document must be carried)
- **Get a replacement** when it was lost or stolen: new number, the old one becomes invalid
- **Report** a document lost or stolen, or **report it found again**
- **Hand in** their own cards that are no longer valid
- **Add a class** gained after the card was printed (runs a renewal)

The photo is taken at the counter. A suspended, revoked or seized document blocks the counter for that type. **Badges are never issued here**: they come from `/documents issue` or the `Issue` export, see [Create a custom document](/jaksam-identity/guides/custom-documents).

<Note>
  A card that isn't the player's own gets the same answer whether it belongs to someone else or is forged, so the office can't be used to test forgeries.
</Note>

### Configuration

Offices are set in `Config.Offices` (`config/office.lua`), or placed in game on the office page of `/documents config`.

```lua
Config.Offices = {
    payAccount = 'money',       -- 'money' (cash) | 'bank'
    pedDistance = 40.0,         -- a counter NPC exists only while the player is this close (metres)
    fees = {                    -- per document type; 0 = free
        id_card = { first = 100, renew = 50, replace = 150 },
        drive = { first = 250, renew = 100, replace = 300 },
        weapon = { first = 1000, renew = 400, replace = 1200 },
    },
    locations = {
        { label = L('office_city_hall'), coords = vec4(-517.63, -251.57, 35.67, 207.0), model = 'a_f_y_business_01',
          documents = { 'id_card', 'drive' }, blip = { sprite = 498, color = 0, scale = 0.7 } },
    },
}
```

Fees are paid only after the photo and the issue succeed.

<Tip>
  You can open one office per authority, for example a DMV counter that only handles `drive` and a police counter that only handles `weapon`.
</Tip>

## esx_dmvschool (ESX only)

esx_dmvschool adds the licence after a passed test but hands out no card. With `Config.DmvSchool` on:

- the **first driver licence is issued right after the test**, with a photo taken there and no fee (the school charged already)
- a class passed later is **printed on the licence the player carries** (same number, expiry and photo)
- without the card on them, the player is told to visit the office, which adds it

```lua
Config.DmvSchool = {
    enabled = true,
    document = 'drive',         -- the document type its licences are classes of
}
```

<Warning>
  The event `esx_dmvschool:addLicense` is not checked on the server by esx_dmvschool, so a cheating client can grant itself any licence with it. Secure the event in esx_dmvschool, or set `Config.DmvSchool.enabled = false`, on a live server.
</Warning>

## QBCore and Qbox city hall

On the QBCore version, what qb-core, qbx_core and qb-cityhall / qbx_cityhall hand out becomes a registered document of the character. qbx_cityhall issues it with a photo taken there. On Qbox, remove `qbx_idcard`: Jaksam Identity answers in its place.
