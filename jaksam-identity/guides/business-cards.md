---
title: "Business cards"
description: "Let every job print its own business cards with name, title, phone number and a free line."
icon: "address-card"
---

Every job prints its own business cards, in its own design. Players open the print dialog with `/businesscards` and get a stack of cards with:

- their name
- an editable title
- their phone number (prefilled from RoadPhone when `Config.Bridge.phone = 'roadphone'`)
- one free line

Business cards have no register and no serial. A business card can be looked at, shown, or handed over to the nearest player.

## Configuration

`Config.BusinessCards` in `config/business.lua`:

```lua
Config.BusinessCards = {
    item = 'business_card',
    command = 'businesscards',   -- opens the print dialog
    amount = 10,                 -- cards per print
    price = 50,                  -- cash per print
    maxTitle = 32,
    maxPhone = 20,
    maxText = 60,
    excludeJobs = { unemployed = true },
    jobs = {
        police = { title = 'LOS SANTOS POLICE DEPARTMENT', header = 'To Protect and to Serve', emblem = 'shield', primary = '#0b1f3a', secondary = '#f5f6f8', accent = '#d4af37' },
    },
    default = { header = 'Los Santos', emblem = 'star', primary = '#2b3440', secondary = '#f6f6f4', accent = '#c8a24a' },
}
```

A job without an entry in `jobs` gets the `default` design with its job label as title. Jobs in `excludeJobs` cannot print.

<Info>
  To show a phone number from another phone script, edit `bridge/phone.lua`. See [Phone number](/jaksam-identity/server/hooks/phone-number).
</Info>
