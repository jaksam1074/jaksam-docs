---
title: "Installation"
description: "Install Blips Creator on your FiveM server."
icon: "download"
---

The installation of the script is extremely easy.

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
    The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `blips_creator/sql/` folder.
  </Step>
  <Step title="Configure the options">
    Configure the options in the config files (be sure to read the comments, they'll explain everything).
  </Step>
  <Step title="Open the menu">
    To open the menu, press `SPACE BAR` while on the in-game big map.
  </Step>
</Steps>

You are ready to go! Enjoy the script 😁

<Note>
  Once the database has been successfully configured, you can optionally remove the SQL files from `blips_creator/sql/`, so the script won't try to set it up again each time it starts.
</Note>
