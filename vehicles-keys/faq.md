---
title: "FAQ"
description: "Frequently asked questions specific to Vehicles Keys."
icon: "circle-question"
---

This page has FAQs related **only to this script** — be sure to also check the [common FAQ](/jaksams-scripts/common-faq) for other issues.

<AccordionGroup>
  <Accordion title="Hitch warning / Performance">
    If your server is showing hitches/performance issues, it's because the option `CONTINUOUSLY_REFRESH_PLAYERS_OWNED_VEHICLES` is enabled in `vehicles_keys/integrations/sv_integrations.lua`.

    If you disable the option, it won't cause performance issues anymore, but you'll have to use the exports from the documentation to refresh a player's owned vehicles (for example after they buy a new vehicle from a shop).

    See the [fix hotwiring bought car](/vehicles-keys/fix-hotwiring-bought-car) page for premade **examples**.

    <Note>
      Integration with other external scripts is completely up to you.
    </Note>
  </Accordion>

  <Accordion title="Cannot enter vehicle">
    If you can't enter a vehicle after destroying its window, it means you still have the `qb-vehicleskeys` script started.

    Remove it to solve the issue.
  </Accordion>
</AccordionGroup>
