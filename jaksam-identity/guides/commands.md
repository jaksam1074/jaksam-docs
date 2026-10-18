---
title: "Commands"
description: "Full list of the /documents admin commands and the player commands of Jaksam Identity."
icon: "slash-forward"
---

## Who can use them

`/documents <subcommand>` works from the server console, for players with the ACE `jksm_identity.admin`, and for the framework groups in `Config.AdminGroups`. Without a subcommand it lists them all.

```cfg
add_ace group.admin jksm_identity.admin allow
```

The command name is `Config.AdminCommand` (default `documents`).

## Admin commands

| Subcommand | What |
| --- | --- |
| `config` | Open the [settings in game](/jaksam-identity/guides/settings-in-game) |
| `issue <playerId> <type> [nophoto] [force] [grant] [grant:<licence type>]` | Issue a real document |
| `check <serial>` | Register check as an authority sees it |
| `truth <serial>` | Admin view: real, forged (with quality and maker) or unknown |
| `license <playerId> list \| add <type> \| remove <type>` | Licences of a character |
| `forge <playerId> <type> <quality 0-100> [nophoto] [copy:<serial>]` | Give a forgery |
| `workshop <job> \| leave` | Enter or leave a workshop |
| `exit <playerId> \| all` | Send players out of the workshops |
| `toner <job> <prints>` | Set the printer toner of a workshop |
| `raid [<workshop> [end \| unseal \| reset]]` | List raids and seals, end a raid, lift a seal, clear the wait until the next raid |
| `order <job> <type> <amount> [low\|normal\|urgent] [assignee]` | Create an order |
| `orders <job>` | List the orders of a workshop |
| `ordercmd <job> <id> <action> [value]` | Manage an order |
| `demo on \| off \| refill` | Demo mode for showcases (`Config.Demo`) |

### Issue options

| Option | Effect |
| --- | --- |
| `nophoto` | Issue without taking a photo |
| `force` | Issue even if the licence or job is missing |
| `grant` | Also give the character every licence of the document |
| `grant:<licence type>` | Also give the character one licence, for example `grant:drive_truck` |

```bash
/documents issue 12 id_card            # ID card with photo for player 12
/documents issue 12 drive grant        # driver licence, granting the licence first
/documents check SAAB1234567           # what the police would see
/documents forge 12 drive 80           # a forged driver licence of quality 80
```

<Note>
  With `Config.Debug = true` there are also measuring commands (`/jksm_pos`, `/jksm_aim`, ...) and test subcommands, for admins only. Turn `Config.Debug` off on a live server: then they do not exist.
</Note>

## Player commands

| Command | What |
| --- | --- |
| `/businesscards` | Print business cards for your job, see [Business cards](/jaksam-identity/guides/business-cards) |
