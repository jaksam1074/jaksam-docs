---
title: "Cartera de RoadPhone"
description: "Muestra los documentos que lleva un jugador en la cartera de RoadPhone, o en cualquier otro script de móvil."
icon: "mobile-screen"
---

Si tu RoadPhone tiene el modo de cartera `jksm_identity`, pon en el `config.lua` de RoadPhone:

```lua
Config.Wallet = {
    Mode = 'jksm_identity',
    IdentityResource = 'jksm_identity',
    -- ...
}
```

La cartera muestra entonces los documentos que lleva el jugador con foto y datos impresos. Mostrar uno abre la tarjeta 3D para el otro jugador.

## Qué muestra la cartera

Como una cartera de verdad, solo lo que el jugador lleva encima:

- el inventario principal
- los contenedores de `Config.WalletContainers` (por defecto `{ 'wallet' }`), no los montones de ID

Un documento falso o robado muestra lo que lleva impreso: nunca se consulta el registro.

<Info>
  - **ox_inventory:** una cartera solo cuenta si es un contenedor de ox (`setContainerProperties`) incluido en `Config.WalletContainers`.
  - **qb-inventory:** no tiene contenedores, así que la cartera solo lee el inventario principal.
</Info>

## Otros scripts de móvil

Otros scripts de móvil pueden hacer lo mismo con dos exports de servidor:

- [Get wallet documents](/es/jaksam-identity/server/wallet/get-wallet-documents): los documentos que lleva el jugador, como datos de tarjeta
- [Show document](/es/jaksam-identity/server/wallet/show-document): muestra un documento que lleva a un jugador cercano como tarjeta 3D
