---
title: "Hooks"
description: "Funciones de servidor editables de Jaksam Identity: permisos, dispatch de redadas, log de admin y número de teléfono."
icon: "code"
---

Esta página lista los hooks del **lado del servidor** de Jaksam Identity. Están en `editable/server.lua` y `bridge/phone.lua`, que quedan abiertos en la versión con escrow. Cambia el contenido, pero conserva los nombres de las funciones y los argumentos.

<CardGroup cols={2}>
  <Card title="Can issue" icon="user-check" href="/es/jaksam-identity/server/hooks/can-issue">
    Decide quién puede expedir un documento real.
  </Card>

  <Card title="Can enter workshop" icon="door-open" href="/es/jaksam-identity/server/hooks/can-enter-workshop">
    Añade tus propias condiciones para entrar en un taller de falsificación.
  </Card>

  <Card title="Can raid" icon="building-shield" href="/es/jaksam-identity/server/hooks/can-raid">
    Añade tus propias condiciones para reventar la puerta de un taller.
  </Card>

  <Card title="On raid" icon="tower-broadcast" href="/es/jaksam-identity/server/hooks/on-raid">
    Envía un aviso de dispatch o tu propia alarma cuando una redada avanza.
  </Card>

  <Card title="On log" icon="clipboard-list" href="/es/jaksam-identity/server/hooks/on-log">
    Envía cada línea del registro de admin a Discord o a un servicio de logs.
  </Card>

  <Card title="Phone number" icon="phone" href="/es/jaksam-identity/server/hooks/phone-number">
    Imprime el número de otro script de móvil en las tarjetas de visita.
  </Card>
</CardGroup>

`Editable.OnIssued` y `Editable.OnForged` reciben los mismos argumentos que los eventos [Document issued](/es/jaksam-identity/server/events/document-issued) y [Document forged](/es/jaksam-identity/server/events/document-forged).
