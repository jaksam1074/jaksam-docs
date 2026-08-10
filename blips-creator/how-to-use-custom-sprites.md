---
title: "How to use custom sprites"
description: "Replace the default blip sprites with your own custom icons."
icon: "image"
---

Blips Creator offers an extremely easy way to replace blip sprites.

<Steps>
  <Step title="Choose an icon">
    Choose a `.png` icon you want to use (64x64px is best).
  </Step>
  <Step title="Open the sprites folder">
    Go to the `blips_creator/_sprites/REPLACEABLE` folder.
  </Step>
  <Step title="Mark the sprite to replace">
    Choose a sprite to replace, copy its name, and add a `#` before the name (so it's easier to find later if needed).
  </Step>
  <Step title="Add your icon">
    Place the new icon with the same name as the old sprite.
  </Step>
  <Step title="Restart the script">
    Restart Blips Creator **2 times**.
  </Step>
</Steps>

## Example with images

In this example, the green logo is replaced with the red sprite.

<Frame caption="blips_creator/_sprites/REPLACEABLE folder">
  ![REPLACEABLE folder](/images/immagine-1.png)
</Frame>

<Frame caption="Copy the file name">
  ![Copy the file name](/images/immagine-8.png)
</Frame>

<Frame caption='Add a "#" before the name'>
  ![Add a hash before the name](/images/immagine-2.png)
</Frame>

<Frame caption="Rename your new icon file name">
  ![Rename the new icon file](/images/immagine-4.png)
</Frame>

<Frame caption="Final result">
  ![Final result](/images/immagine-7.png)
</Frame>

Now restart the script **2 times** and the sprite is updated.
