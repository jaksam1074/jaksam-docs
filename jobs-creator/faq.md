---
title: "FAQ"
description: "Frequently asked questions specific to Jobs Creator, covering animations, salaries, outfits, and common setup errors."
icon: "circle-question"
---

This page has FAQs related **ONLY to this script**. Be sure to also check the [common FAQ](https://jaksam.mintlify.site/jaksams-scripts/common-faq) for other issues.

<AccordionGroup>
  <Accordion title="How to change animations">
    [This is a list of usable animations](https://alexguirre.github.io/animations-list/)

    - Bigger text is the animation dictionary
    - Smaller text is the animation name

    [This is the list of usable scenarios](https://wiki.rage.mp/index.php?title=Scenarios)

    The main difference between scenarios and animations is that a scenario usually has an object attached to the animation.

    _It's not possible to use external animations._

    <Note>
      Not all animations in the lists work.
    </Note>
  </Accordion>

  <Accordion title="How to lock jobs vehicles">
    To lock vehicles you have 2 possibilities:

    1. Use the events and exports from the script documentation to integrate your own car lock script
    2. Use **jaksam's Vehicles Keys**, which has Jobs Creator integration included

    _Note: external script integration is completely down to you._
  </Accordion>

  <Accordion title="How does Jobs Creator handle salaries/wages?">
    Jobs Creator doesn't handle salaries, this is because the framework script does it:

    - For ESX, `es_extended` and `esx_society` scripts handle the salaries
    - For QBCore, `qb-core` handles the salaries

    So you will be able to **define** the salaries in Jobs Creator, but it's the framework that pays out the money.
  </Accordion>

  <Accordion title='How to fix "Couldnt create marker" error'>
    This issue is caused by something wrong in the `job_data` table of the database.

    Possible solutions:

    1. Delete the `job_data` table from the database and restart the script/server
    2. If the `id` column of the `job_data` table doesn't have **AUTO INCREMENT** as default value, set that column's default value to **AUTO INCREMENT**
  </Accordion>

  <Accordion title="Why outfits features don't work?">
    If the outfits features don't work, it's because you don't have the required dependencies:

    - On ESX, you must have the `esx_skin` and `skinchanger` scripts installed
    - On QBCore, you must have the `qb-clothing` script installed

    Jobs Creator has integration for [**illenium-appearance**](https://github.com/iLLeniumStudios/illenium-appearance), which should work on both frameworks.
  </Accordion>

  <Accordion title="Weapon upgrader doesn't work">
    In case the weapon upgrader marker doesn't work, these are 2 possible reasons:

    1. You are using an addon weapon, but haven't configured it properly in the `es_extended` script
    2. Your inventory edits the standard behavior of **ESX/QBCore**, so in this case you must use your own inventory instead of Jobs Creator for weapon components and tints
  </Accordion>

  <Accordion title="Edit vehicle labels in garages">
    Jobs Creator retrieves vehicle labels through FiveM natives, so to have custom labels, you'll have to configure them in your addon vehicle script.

    There are multiple guides on the FiveM forums on how to configure addon vehicle display names.
  </Accordion>

  <Accordion title="QBCore doesn't recognize Jobs Creator jobs">
    Usually you are not required to add any code. Despite this, a different script start order may cause other scripts to not recognize Jobs Creator jobs on QBCore.

    **How can I fix this?**

    The solution is very easy: add the following event **client side and server side** in the script that is not recognizing the Jobs Creator jobs.

    ```lua
        -- jaksam's Jobs Creator integration
        AddEventHandler('jobs_creator:injectJobs', function(jobs)
            -- Assign the new jobs to the QBCore object, the following line depends on how your script is structured
            QBCore.Shared.Jobs = jobs
        end)
    ```
  </Accordion>
</AccordionGroup>