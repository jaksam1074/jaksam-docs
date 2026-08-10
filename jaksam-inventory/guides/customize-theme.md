---
title: "Customize Default Theme"
description: "Set a custom default theme for all players on your server, step-by-step"
icon: "palette"
---

Want every player to have the same default theme? Here's how to do it, step-by-step.

<Steps>
  <Step title="Open your inventory">
    Press **F2** in-game to open your inventory.
  </Step>
  <Step title="Open the theme editor">
    Click the **Theme** button (bottom right corner).

    <Frame>
      ![Inventory theme customization 1](/images/inventory-theme-1.jpg)
    </Frame>
  </Step>
  <Step title="Customize and save">
    Change the colors and styles as you like, then hit **Save**.
  </Step>
  <Step title="Select your theme">
    Make sure your custom theme is selected.

    <Frame>
      ![Inventory theme customization 2](/images/inventory-theme-2.jpg)
    </Frame>
  </Step>
  <Step title="Open the console">
    Press **F8** to open the console, then type:

    ```bash
        admintheme
    ```
  </Step>
  <Step title="Copy the theme code">
    You'll see a bunch of code.

    <Note>
      Copy _everything_ between `COPY FROM THE LINE BELOW` and `COPY TILL THE LINE ABOVE` — don't miss the edges.
    </Note>

    <Frame>
      ![Inventory theme customization 3](/images/inventory-theme-3.jpg)
    </Frame>
  </Step>
  <Step title="Open the theme file">
    Go to the server files and open:

    ```text
        jaksam_inventory/dist/assets/variables.css
    ```
  </Step>
  <Step title="Paste and replace">
    Paste what you copied, replacing **everything** in that file.
  </Step>
  <Step title="Restart">
    Restart the script or reload the server.
  </Step>
</Steps>

<Tip>
  That's it! Now everyone's default theme will use your custom colors and settings (unless they change it themselves).
</Tip>