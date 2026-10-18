---
title: "Serveur"
description: "Exports, events et hooks côté serveur disponibles dans Jaksam Identity."
icon: "server"
---

Cette page liste les exports, events et hooks **côté serveur** disponibles dans Jaksam Identity, pour les scripts de MDT, d'auto-école, de téléphone et de jobs.

<CardGroup cols={2}>
  <Card title="Registre" icon="address-book" href="/fr/jaksam-identity/server/register">
    Contrôle, délivre et change le statut des vrais documents.
  </Card>

  <Card title="Portefeuille" icon="wallet" href="/fr/jaksam-identity/server/wallet">
    Lis les documents qu'un joueur porte et montre-en un, pour les scripts de téléphone.
  </Card>

  <Card title="Events" icon="bolt" href="/fr/jaksam-identity/server/events">
    Déclenchés quand un document est délivré, falsifié ou change de statut.
  </Card>

  <Card title="Hooks" icon="code" href="/fr/jaksam-identity/server/hooks">
    Fonctions modifiables dans `editable/server.lua` et `bridge/phone.lua`.
  </Card>
</CardGroup>

<Note>
  Le registre ne contient que les **vrais** documents. Un faux document n'y apparaît jamais : le contrôle d'un faux numéro renvoie "aucune fiche", exactement comme la police le verrait.
</Note>
