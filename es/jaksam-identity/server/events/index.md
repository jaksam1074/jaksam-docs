---
title: "Events"
description: "Eventos de servidor que activa Jaksam Identity cuando un documento se expide, se falsifica o cambia de estado."
icon: "bolt"
---

Esta página lista los eventos del **lado del servidor** que activa Jaksam Identity. Son eventos locales de servidor: escúchalos con `AddEventHandler` en otro script de servidor.

<CardGroup cols={2}>
  <Card title="Document issued" icon="id-card" href="/es/jaksam-identity/server/events/document-issued">
    Se activa después de expedir un documento real.
  </Card>

  <Card title="Document forged" icon="print" href="/es/jaksam-identity/server/events/document-forged">
    Se activa después de hacer una falsificación.
  </Card>

  <Card title="Status changed" icon="tag" href="/es/jaksam-identity/server/events/status-changed">
    Se activa después de que cambie el estado en el registro de un documento.
  </Card>
</CardGroup>
