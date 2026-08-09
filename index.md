---
title: "Home"
description: "Documentation for all of jaksam's scripts"
mode: "wide"
---

Here you will find all documentation for jaksam's scripts. Some pages may require coding knowledge.

## How to use the documentation

Most of the scripts will have a folder named **integrations**, where you can add the integration code at the bottom of the files. So most of the time, you will only need to add your code inside these files, not in other scripts.

<Tip>
  Be sure to read the comments carefully, they'll explain everything you need right above the lines of code.
</Tip>

### Integration files

<CardGroup cols={4}>
  <Card title="cl_integrations.lua" icon="laptop">
    Code for **client side** scripts, for example replacing notifications or the progress bar. Usually where you insert code from the `Client` category of the documentation.
  </Card>

  <Card title="sh_integrations.lua" icon="arrows-left-right">
    Code that runs **both on client and server side**, usually external script names, so you can edit them if your server uses a different name than the default one.
  </Card>

  <Card title="sv_integrations.lua" icon="server">
    Code for **server side** scripts. Usually where you insert code from the `Server` category of the documentation.
  </Card>

  <Card title="_modules" icon="folder">
    Our scripts have a `_modules` folder to easily replace default features like notify, progress bar, stash, or logs. Duplicate an existing module inside it to create your own.
  </Card>
</CardGroup>

<Info>
  If you're looking for an option that you can't find in the normal config/settings, it's probably inside the integrations files.
</Info>