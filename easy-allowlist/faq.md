---
title: "FAQ"
description: "Frequently asked questions specific to Easy Allowlist & Queue."
icon: "circle-question"
---

This page has FAQs related **only to this script** — be sure to also check the [common FAQ](/jaksams-scripts/common-faq) for other issues.

<AccordionGroup>
  <Accordion title="How to add myself to the allowlist">
    The script will automatically detect if the allowlist is completely empty, so you'll be automatically whitelisted the first time you join.

    To whitelist manually, send the allowlist request to your server and then use the command `add_allowlist YourRequestIdHere` in the server console.
  </Accordion>

  <Accordion title="Stuck on 'deferring connection...'">
    If when you connect to your server, Easy Allowlist says `deferring connection...` and gets stuck without any error at all, try:

    <Steps>
      <Step title="Open the deferrals file">
        Open the file `easy_allowlist/server/deferrals.lua`.
      </Step>
      <Step title="Find the wait">
        Search for the `Citizen.Wait(500)` code.
      </Step>
      <Step title="Increase the wait">
        Edit it from `Citizen.Wait(500)` to `Citizen.Wait(10000)` or higher if it still doesn't work.
      </Step>
      <Step title="Save and restart">
        Save the file and restart the script.
      </Step>
    </Steps>
  </Accordion>
</AccordionGroup>
