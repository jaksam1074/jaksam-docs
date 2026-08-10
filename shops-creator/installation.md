---
title: "Installation"
description: "Install Shops Creator on your FiveM server."
icon: "download"
---

The installation of the script is extremely easy.

## Requirements

- The [cracking safe script](https://github.com/VHall1/pd-safe) by [VHall1](https://github.com/VHall1) (if you want the safe-cracking feature)

<Danger>
  Do **NOT** use FileZilla to upload the files, otherwise the script will **NOT** work.

  Use [WinSCP](https://winscp.net/eng/download.php) instead.
</Danger>

<Steps>
  <Step title="Download and extract">
    Download the script and extract it in your resources.
  </Step>
  <Step title="Add to auto start">
    Add the script in your auto start (example: `server.cfg`).
  </Step>
  <Step title="Database setup">
    The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `shops_creator/sql/` folder.
  </Step>
  <Step title="Cracking safe script">
    Download and start the [cracking safe script](https://github.com/VHall1/pd-safe) _(credits to [VHall1](https://github.com/VHall1))_.
  </Step>
</Steps>

You are ready to go! Enjoy the script 😁

## Verification

Open `/shopscreator` in-game. If the menu opens, the script is running correctly.

<Note>
  Once the database has been successfully configured, you can optionally remove the SQL files from `shops_creator/sql/`, so the script won't try to set it up again each time it starts.
</Note>
