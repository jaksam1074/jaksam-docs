---
title: "Server"
description: "Exports, events y hooks del lado del servidor disponibles en Jaksam Identity."
icon: "server"
---

Esta página lista los exports, events y hooks del **lado del servidor** disponibles en Jaksam Identity, para scripts de MDT, autoescuela, móvil y trabajos.

<CardGroup cols={2}>
  <Card title="Register" icon="address-book" href="/es/jaksam-identity/server/register">
    Consulta, expide y cambia el estado de documentos reales.
  </Card>

  <Card title="Wallet" icon="wallet" href="/es/jaksam-identity/server/wallet">
    Lee los documentos que lleva un jugador y muestra uno, para scripts de móvil.
  </Card>

  <Card title="Events" icon="bolt" href="/es/jaksam-identity/server/events">
    Se activan cuando un documento se expide, se falsifica o cambia de estado.
  </Card>

  <Card title="Hooks" icon="code" href="/es/jaksam-identity/server/hooks">
    Funciones editables en `editable/server.lua` y `bridge/phone.lua`.
  </Card>
</CardGroup>

<Note>
  El registro solo contiene documentos **reales**. Un documento falso nunca aparece en él: la consulta del registro de un número falso devuelve "sin registro", exactamente como lo vería la policía.
</Note>
