---
title: "Common FAQ"
description: "Frequently asked questions shared across all scripts"
icon: "circle-user-circle-question"
---

This page contains common FAQ shared for all scripts. If your issue is not on this page, be sure to check the FAQ of the script you are having issues with.

<AccordionGroup>
  <Accordion title="Crash">
    Crashes can be caused by 2 things:

    - You have to whitelist these object models in your anticheat: `L1_1`, `GetHashKey('L1_1')`, `2116969379`
    - If you still experience crashes after whitelisting those object models in your anticheat, you can refer to [this page](/trouble-shooting)

    _If you don't know how to whitelist object models in your anticheat, ask your anticheat creator._
  </Accordion>

  <Accordion title="Attempted to index a nil value (field 'ESX')">
    If you have this error, it means the script couldn't retrieve the shared object of ESX.

    This error might be caused by other errors you have in your server/F8 console, which happen before it does.

    If you don't have any other error before that one, you can refer to [this page](/trouble-shooting).
  </Accordion>

  <Accordion title='How to fix "missing menu_default" error'>
    To fix the error, simply read the installation tutorial of the script.
  </Accordion>

  <Accordion title="Objects/Props not spawning">
    If the props don't spawn, it's very probably an issue with your anticheat.

    Be sure to whitelist all the props in your anticheat. If you don't know how, ask your anticheat creator.
  </Accordion>

  <Accordion title="Can't receive ANY item">
    If you have already tried with different items and you can't receive any of them, check [this page](/trouble-shooting).
  </Accordion>

  <Accordion title="Can't receive WEAPONS ONLY">
    If only weapons cause issues but items work fine, these are the possible reasons:

    - On ESX, it's most likely because your server doesn't support the standard ESX method `xPlayer.addWeapon`
    - On QBCore, it may be that your inventory is changing the default behaviour of `qb-inventory`

    This is not an issue which depends on the script, but on your framework/inventory, and cannot be solved by us — the standard methods must work.
  </Accordion>

  <Accordion title="How to replace default notifications">
    To replace the notifications of any script, you can refer to the documentation of the script. It has events that allow you to disable the default one and call an external one.

    _Note: external script integration is completely down to you._
  </Accordion>

  <Accordion title="How to replace the default progress bar">
    To replace the progress bar of any script, you can refer to the documentation of the script. It has events that allow you to disable the default one and call an external one.

    _Note: external script integration is completely down to you._
  </Accordion>

  <Accordion title="Script transfers">
    Scripts can be transferred one time only through the FiveM keymaster, by using the side button instead of "Download". There are no manual revokes or manual transfers in any situation at all.
  </Accordion>

  <Accordion title="Refunds">
    Purchases in jaksam's store are final, this applies to any situation — wrong framework, wrong accounts, etc. So in case of refunds, unfortunately we cannot help with them at all.
  </Accordion>
</AccordionGroup>