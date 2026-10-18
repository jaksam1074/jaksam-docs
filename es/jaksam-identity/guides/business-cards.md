---
title: "Tarjetas de visita"
description: "Deja que cada trabajo imprima sus propias tarjetas de visita con nombre, cargo, número de teléfono y una línea libre."
icon: "address-card"
---

Cada trabajo imprime sus propias tarjetas de visita, con su propio diseño. Los jugadores abren el diálogo de impresión con `/businesscards` y reciben un montón de tarjetas con:

- su nombre
- un cargo editable
- su número de teléfono (rellenado desde RoadPhone si `Config.Bridge.phone = 'roadphone'`)
- una línea libre

Las tarjetas de visita no tienen registro ni número. Una tarjeta de visita se puede mirar, mostrar o entregar al jugador más cercano.

## Configuración

`Config.BusinessCards` en `config/business.lua`:

```lua
Config.BusinessCards = {
    item = 'business_card',
    command = 'businesscards',   -- opens the print dialog
    amount = 10,                 -- cards per print
    price = 50,                  -- cash per print
    maxTitle = 32,
    maxPhone = 20,
    maxText = 60,
    excludeJobs = { unemployed = true },
    jobs = {
        police = { title = 'LOS SANTOS POLICE DEPARTMENT', header = 'To Protect and to Serve', emblem = 'shield', primary = '#0b1f3a', secondary = '#f5f6f8', accent = '#d4af37' },
    },
    default = { header = 'Los Santos', emblem = 'star', primary = '#2b3440', secondary = '#f6f6f4', accent = '#c8a24a' },
}
```

Un trabajo sin entrada en `jobs` recibe el diseño `default` con su etiqueta de trabajo como título. Los trabajos de `excludeJobs` no pueden imprimir.

<Info>
  Para mostrar un número de teléfono de otro script de móvil, edita `bridge/phone.lua`. Mira [Número de teléfono](/es/jaksam-identity/server/hooks/phone-number).
</Info>
