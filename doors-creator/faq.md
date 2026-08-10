---
title: "FAQ"
description: "Frequently asked questions specific to Doors Creator."
icon: "circle-question"
---

This page has FAQs related **only to this script** — be sure to also check the [common FAQ](/jaksams-scripts/common-faq) for other issues.

<AccordionGroup>
  <Accordion title="Can't select a door">
    If you can't select a door, it means the door model is not in the allowed doors list.

    To add the door model to the list, press **H** while selecting the door.

    If you still can't select the door after pressing H, these are the possible reasons:

    - You have a script that adds a weapon to your character
    - The door isn't usable for some reason — if it's a modded MLO, that's probably the cause
  </Accordion>

  <Accordion title="Vault door not working">
    If a certain door isn't working with the vault option, try **both** the ratio and heading options.

    For the heading, you'll have to find which value fits that door best on your own (0-360 are the min/max values), or use the built-in button in the script to find it.

    Be sure to try different speeds (like a slower speed).

    <Note>
      If a door doesn't work at all, there is nothing that can be done.
    </Note>
  </Accordion>

  <Accordion title="Doors not locked after restart">
    If a door isn't locked when it should be after a script/server restart, it means you enabled the option to save the door lock state in the script's menu settings.
  </Accordion>

  <Accordion title="I can't confirm a new door">
    If you can't confirm a new door with the ENTER key, you can edit the keybinds in the `integrations/cl_integrations.lua` file.
  </Accordion>
</AccordionGroup>
