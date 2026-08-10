---
title: "Installation"
description: "Install Doors Creator on your FiveM server."
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
    The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `doors_creator/sql/` folder.
  </Step>
  <Step title="Lockpicking script">
    Download and start the [lockpicking script](https://github.com/baguscodestudio/lockpick) _(credits to [baguscodestudio](https://github.com/baguscodestudio/lockpick))_.
  </Step>
  <Step title="Add the lockpick item">
    Add the `doors_lockpick` item to your items list, as you would for any script.
  </Step>
  <Step title="Configure the script">
    Configure the script from the in-game admin menu `/doorscreator`.
  </Step>
</Steps>

You are ready to go! Enjoy the script 😁

<Note>
  Once the database has been successfully configured, you can optionally remove the SQL files from `doors_creator/sql/`, so the script won't try to set it up again each time it starts.
</Note>
