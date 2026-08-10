---
title: "FAQ"
description: "Frequently asked questions specific to Drugs Creator."
icon: "circle-question"
---

This page has FAQs related **only to this script** — be sure to also check the [common FAQ](/jaksams-scripts/common-faq) for other issues.

<AccordionGroup>
  <Accordion title="Drugs effects not working">
    If the effects aren't working, it means the `ESX.RegisterUsableItem` function of your `es_extended` isn't working properly.

    You can still manually register/trigger effects by using the [manually start drugs effects](/drugs-creator/client/manually-start-drugs-effects) event.

    On both **ESX** and **QBCore**, an anticheat may interfere with drug effects.

    <Note>
      This isn't something that depends on the script, and we can't solve it for you.
    </Note>
  </Accordion>

  <Accordion title="Bad performance">
    If you're having server-side performance issues with Drugs Creator, it's most likely because of NPC selling, which requires refreshing all players' inventories to be able to prompt the `Press E to sell drugs` dialog.

    To improve performance, enable the corresponding option in the in-game script settings, so it will use the closest NPC or spawn one (depending on your configuration).
  </Accordion>
</AccordionGroup>
