---
title: "Installation"
description: "Install Easy Allowlist & Queue on your FiveM server."
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
    The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `easy_allowlist/sql/` folder.
  </Step>
  <Step title="Whitelist yourself">
    To add yourself to the allowlist, use the `add_allowlist REQUEST_ID` command in the server console after you have sent the request.
  </Step>
  <Step title="Configure in-game settings">
    Set up the in-game settings by also following this guide.
  </Step>
</Steps>

You are ready to go! Enjoy the script 😁

## Verification

Run `add_allowlist REQUEST_ID` in the server console (per the "Whitelist yourself" step above). If the command is recognized and runs without an unknown-command error, the script is running correctly.

<Note>
  Once the database has been successfully configured, you can optionally remove the SQL files from `easy_allowlist/sql/`, so the script won't try to set it up again each time it starts.
</Note>
