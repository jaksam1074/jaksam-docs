---
title: "RoadPhone wallet"
description: "Show the documents a player carries in the RoadPhone wallet, or in any other phone script."
icon: "mobile-screen"
---

If your RoadPhone has the wallet mode `jksm_identity`, set in RoadPhone's `config.lua`:

```lua
Config.Wallet = {
    Mode = 'jksm_identity',
    IdentityResource = 'jksm_identity',
    -- ...
}
```

The wallet then lists the documents the player carries with photo and printed data. Showing one opens the 3D card for the other player.

## What the wallet lists

Like a real wallet, only what the player physically carries:

- the main inventory
- the containers listed in `Config.WalletContainers` (default `{ 'wallet' }`), not ID stacks

A forged or stolen document shows what is printed on it: the register is never asked.

<Info>
  - **ox_inventory:** a wallet only counts if it is an ox container (`setContainerProperties`) listed in `Config.WalletContainers`.
  - **qb-inventory:** it has no containers, so the wallet reads the main inventory only.
</Info>

## Other phone scripts

Other phone scripts can do the same with two server exports:

- [Get wallet documents](/jaksam-identity/server/wallet/get-wallet-documents): the documents the player carries, as card data
- [Show document](/jaksam-identity/server/wallet/show-document): shows a carried document to a player nearby as the 3D card
