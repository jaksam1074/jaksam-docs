---
title: "Editable files"
description: "Los archivos de Jaksam Identity que quedan abiertos en la versión con escrow: config, locales, bridge y hooks editables."
icon: "file-pen"
---

Jaksam Identity no tiene carpeta `integrations`. Todo lo que puedes cambiar queda abierto en la versión con escrow, en estas carpetas:

| Carpeta | Qué contiene |
| --- | --- |
| `config/` | Todos los ajustes |
| `locales/` | Textos, `Config.Locale` elige el idioma |
| `bridge/` | Inventario, target, notificaciones, móvil (el bridge del framework en `bridge/framework/` va con escrow) |
| `editable/` | Hooks: `CanIssue`, `OnIssued`, `CanEnterWorkshop`, `CanRaid`, `OnRaid`, `OnForged`, `OnLog`, `SkillCheck`, `Progress` |
| `install/` | Items del inventario, tipos de item, imágenes, SQL |

## Hooks editables

<CardGroup cols={2}>
  <Card title="editable/server.lua" icon="server" href="/es/jaksam-identity/server/hooks">
    Hooks de servidor: quién puede expedir, entrar en un taller o hacer una redada, y qué pasa tras una expedición, una falsificación, un paso de redada o una línea de log.
  </Card>

  <Card title="editable/client.lua" icon="laptop" href="/es/jaksam-identity/client">
    Hooks de cliente: el skill check de las estaciones de falsificación y la progress bar.
  </Card>
</CardGroup>

Cambia el contenido para adaptarlo a tu servidor, pero **conserva los nombres de las funciones y los argumentos**.

## Bridge

`Config.Bridge` en `config/main.lua` elige los archivos de `bridge/`:

```lua
Config.Bridge = {
    framework = 'esx',          -- ESX version: 'esx' | QBCore version: 'auto' | 'qb' | 'qbox'
    inventory = 'jaksam',       -- 'jaksam' | 'ox_inventory' | 'qb-inventory' (QBCore version)
    target = 'ox_target',       -- 'ox_target' | QBCore version also 'qb-target' | 'auto'
    notify = 'esx',             -- 'esx' | 'qb' | 'qbox' | 'ox_lib' | QBCore version also 'auto'
    phone = 'roadphone',        -- 'roadphone' | 'none'
    menu = 'jksm',              -- 'jksm' (interaction card) | 'ox_lib' (context menu)
}
```

Para soportar otro inventario, el contrato que debe cumplir un bridge de inventario está documentado al principio de `bridge/inventory/jaksam.lua`.
