---
title: "Installation"
description: "Install Farming Creator on your FiveM server with ESX or QBCore."
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
    The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `farming_creator/sql/` folder.
  </Step>
  <Step title="Install menu_default (QBCore only)">
    Download and extract the [menu_default](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) script in your resources, **without renaming it**, and add it to your auto start (example: `server.cfg`).
  </Step>
</Steps>

You are ready to go! Enjoy the script 😁

<Note>
  Once the database has been successfully configured, you can optionally remove the SQL files from `farming_creator/sql/`, so the script won't try to set it up again each time it starts.
</Note>
