---
title: "Events"
description: "Events serveur déclenchés par Jaksam Identity quand un document est délivré, falsifié ou change de statut."
icon: "bolt"
---

Cette page liste les events **côté serveur** déclenchés par Jaksam Identity. Ce sont des events serveur locaux : écoute-les avec `AddEventHandler` dans un autre script serveur.

<CardGroup cols={2}>
  <Card title="Document délivré" icon="id-card" href="/fr/jaksam-identity/server/events/document-issued">
    Déclenché après la délivrance d'un vrai document.
  </Card>

  <Card title="Document falsifié" icon="print" href="/fr/jaksam-identity/server/events/document-forged">
    Déclenché après la fabrication d'un faux.
  </Card>

  <Card title="Statut modifié" icon="tag" href="/fr/jaksam-identity/server/events/status-changed">
    Déclenché après le changement de statut d'un document au registre.
  </Card>
</CardGroup>
