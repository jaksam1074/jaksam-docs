---
title: "Installation"
description: "Install Missions Creator on your FiveM server with ESX or QBCore, including optional minigame scripts."
icon: "download"
---

The installation of the script is extremely easy.

<Danger>
  Do **NOT** use FileZilla to upload the files, otherwise the script will **NOT** work.

  Use [WinSCP](https://winscp.net/eng/download.php) instead.
</Danger>

<Tabs>
  <Tab title="ESX">
    <Steps>
      <Step title="Download and extract">
        Download the script and extract it in your resources.
      </Step>
      <Step title="Download jaksam_core">
        Download `jaksam_core` and extract it in your resources.
      </Step>
      <Step title="Add jaksam_core to auto start">
        Add `jaksam_core` in your auto start (example: `server.cfg`).
      </Step>
      <Step title="Add missions_creator to auto start">
        Start `missions_creator` **after** `jaksam_core`.
      </Step>
      <Step title="Database setup">
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `missions_creator/sql/` folder.
      </Step>
      <Step title="Optional minigame scripts">
        - Download and start the [datacrack minigame script](https://github.com/utkuali/datacrack) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [fingerprint minigame script](https://github.com/utkuali/Finger-Print-Hacking-Game) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(credits to [ultrahacx](https://github.com/ultrahacx))_
      </Step>
    </Steps>

    <Danger>
      If it doesn't work, be sure to use the latest official version of ESX with the required dependencies.
    </Danger>
  </Tab>
  <Tab title="QBCore">
    <Steps>
      <Step title="Download and extract">
        Download the script and extract it in your resources.
      </Step>
      <Step title="Download jaksam_core">
        Download `jaksam_core` and extract it in your resources.
      </Step>
      <Step title="Add jaksam_core to auto start">
        Add `jaksam_core` in your auto start (example: `server.cfg`).
      </Step>
      <Step title="Add missions_creator to auto start">
        Start `missions_creator` **after** `jaksam_core`.
      </Step>
      <Step title="Database setup">
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `missions_creator/sql/` folder.
      </Step>
      <Step title="Optional minigame scripts">
        - Download and start the [datacrack minigame script](https://github.com/utkuali/datacrack) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [fingerprint minigame script](https://github.com/utkuali/Finger-Print-Hacking-Game) _(credits to [utkuali](https://github.com/utkuali))_
        - Download and start the [memory minigame script](https://github.com/ultrahacx/ultra-keypackhack) _(credits to [ultrahacx](https://github.com/ultrahacx))_
      </Step>
    </Steps>
  </Tab>
</Tabs>

You are ready to go! Enjoy the script 😁

## Optional step

After the database is set up correctly, you can delete the files in `missions_creator/sql/` folder, so the script won't try to set up the database each time you start it.
