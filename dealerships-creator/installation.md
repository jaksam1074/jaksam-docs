---
title: "Installation"
description: "Install Dealerships Creator on your FiveM server, including optional automatic vehicle image generation."
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
    The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `dealerships_creator/sql/` folder.
  </Step>
</Steps>

You are ready to go! Enjoy the script 😁

<Note>
  Once the database has been successfully configured, you can optionally remove the SQL files from `dealerships_creator/sql/`, so the script won't try to set it up again each time it starts.
</Note>

## Automatic image creation — Optional

If you want to use automatic vehicle image creation, follow these steps:

<Steps>
  <Step title="Install screenshot-basic">
    Install [screenshot-basic](https://github.com/citizenfx/screenshot-basic) (you probably already have it).
  </Step>
  <Step title="Install yarn">
    Install [yarn](https://github.com/citizenfx/cfx-server-data) (you probably already have it — `resources/[system]/[builders]`).
  </Step>
  <Step title="Install webpack">
    Install [webpack](https://github.com/citizenfx/cfx-server-data) (you probably already have it — `resources/[system]/[builders]`).
  </Step>
  <Step title="Set folder permissions">
    Make sure the `dealerships_creator` folder and the `dealerships_creator/_vehicles_images` folder have read/write permissions (right-click the folders → Properties → enable read (**R**) and write (**W**) permissions).
  </Step>
</Steps>
