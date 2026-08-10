---
title: "Installation"
description: "Install Billing UI on your FiveM server with ESX or QBCore."
icon: "download"
---

The installation of the script is extremely easy.

## Requirements

- **ESX** or **QBCore**
- On ESX, `esx_billing` must be removed (see the warning below)
- On QBCore, the [`menu_default`](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) script

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
      <Step title="Add to auto start">
        Add the script in your auto start (example: `server.cfg`).
      </Step>
      <Step title="Database setup">
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `billing_ui/sql/` folder.
      </Step>
      <Step title="Configure the options">
        Configure the options in the config files (be sure to read the comments, they'll explain everything).
      </Step>
    </Steps>

    <Warning>
      Be sure to remove `esx_billing` to avoid issues.
    </Warning>
  </Tab>
  <Tab title="QBCore">
    <Steps>
      <Step title="Download and extract">
        Download the script and extract it in your resources.
      </Step>
      <Step title="Add to auto start">
        Add the script in your auto start (example: `server.cfg`).
      </Step>
      <Step title="Database setup">
        The script will **automatically** set up the database. In case it doesn't, you can manually run the files in the `billing_ui/sql/` folder.
      </Step>
      <Step title="Configure the options">
        Configure the options in the config files (be sure to read the comments, they'll explain everything).
      </Step>
      <Step title="Install menu_default">
        Download and extract the [menu_default](https://drive.google.com/file/d/1Ezz-d50NIKQZeZJ-RgyclvNG7qC4Nfu8/view?usp=sharing) script in your resources, **without renaming it**, and add it to your auto start (example: `server.cfg`).
      </Step>
    </Steps>
  </Tab>
</Tabs>

You are ready to go! Enjoy the script 😁

## Verification

<Info>
  [TODO: INFORMATION NEEDED] No in-game check for a successful install is documented yet for Billing UI.
</Info>

## Optional step

After the database is set up correctly, you can delete the files in `billing_ui/sql/` folder, so the script won't try to set up the database each time you start it.
