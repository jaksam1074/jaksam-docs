---
title: "Jaksam Identity"
description: "Official documentation for the Jaksam Identity FiveM script: identity documents, licences, citizen offices, forgery workshops and raids."
icon: "id-card"
---

This is the official **Jaksam Identity** documentation.

Jaksam Identity turns identity documents and licences into real inventory items: ID card, driver licence with classes, firearms permit, service badges and business cards, each with a 3D card view. Next to the legal side it adds a full forgery economy, with job-owned workshops, NPC workers, an order queue and police raids.

<CardGroup cols={2}>
  <Card title="Store" icon="cart-shopping" href="https://fivem.jaksam-scripts.com/">
    Purchase or view the script on the jaksam store.
  </Card>

  <Card title="Showcase" icon="play" href="https://youtu.be/3Z_h05D65QI">
    Watch the full feature showcase on YouTube.
  </Card>

  <Card title="Supported Languages" icon="language">
    English, German
  </Card>
</CardGroup>

## What it does

<CardGroup cols={2}>
  <Card title="Documents as items" icon="id-card">
    ID card, driver licence with classes, firearms permit, badges and business cards with a 3D card view (rotate, flip, UV lamp).
  </Card>

  <Card title="Citizen offices" icon="building-columns">
    An NPC at the counter to apply, renew, replace, report a document lost or stolen, and hand in old cards.
  </Card>

  <Card title="Register check" icon="magnifying-glass">
    Authorities see if a document is real, suspended, expired, has revoked classes, or has no record at all.
  </Card>

  <Card title="Forgery workshops" icon="print">
    Job-owned workshops with photo, data entry, printing, laminating, embossing and cutting. Quality decides which flaws show.
  </Card>

  <Card title="NPC workers and orders" icon="users-gear">
    Hire workers, queue orders with priority, manage everything from the boss laptop.
  </Card>

  <Card title="Raids" icon="building-shield">
    Officers break the door open, seize evidence and seal the workshop.
  </Card>
</CardGroup>

## Documentation

<CardGroup cols={2}>
  <Card title="Installation" icon="download" href="/jaksam-identity/installation">
    Get Jaksam Identity installed and running on your server.
  </Card>

  <Card title="Guides" icon="book-open" href="/jaksam-identity/guides/documents-and-register">
    Documents, offices, workshops, raids, settings in game and commands.
  </Card>

  <Card title="FAQ" icon="circle-question" href="/jaksam-identity/faq">
    Frequently asked questions.
  </Card>

  <Card title="Developer Reference" icon="code" href="/jaksam-identity/server">
    Exports, events and hooks for developers.
  </Card>
</CardGroup>

## Framework Support

<CardGroup cols={3}>
  <Card title="ESX" icon="code" href="/jaksam-identity/installation">
    Licences from the esx_license tables, optional esx_dmvschool support.
  </Card>

  <Card title="QBCore" icon="code" href="/jaksam-identity/installation">
    Licences from the character metadata, qb-inventory 2.2 supported.
  </Card>

  <Card title="Qbox" icon="code" href="/jaksam-identity/installation">
    Replaces qbx_idcard, works with qbx_core starter items and qbx_cityhall.
  </Card>
</CardGroup>
