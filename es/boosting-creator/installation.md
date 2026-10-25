---
title: "Instalación"
description: "Instala Boosting Creator en tu servidor de FiveM con ESX, QBCore o Qbox, añade el item del portátil y da el permiso de admin."
icon: "download"
---

Pon **Boosting Creator** en marcha en tu servidor de FiveM.

## Requisitos

| Recurso | Para qué |
| --- | --- |
| `es_extended` **o** `qb-core` / `qbx_core` | Framework |
| `ox_lib` | Callbacks y módulos opcionales |
| `oxmysql` (o `mysql-async`) | Base de datos |
| OneSync | Los autos de los contratos, los guardias y los perseguidores son entidades en red |
| `vehicles_keys` (opcional) | Ganzúa y puente con vehicles_keys, llaves temporales para el auto robado |
| `datacrack`, `utk_fingerprint`, `ultra-keypackhack` (opcional) | Minijuegos de hackeo extra |

<Warning>
  Los autos de los contratos, los guardias, los autos del garaje, el portavehículos y la banda perseguidora los crea el juego del ladrón y los comprueba el servidor. Con `sv_entityLockdown strict` no aparece nada y cada contrato se cancela justo después de empezar.
</Warning>

<Danger>
  **NO** uses FileZilla para subir los archivos, de lo contrario el script **NO** funcionará.

  Usa [WinSCP](https://winscp.net/eng/download.php) en su lugar.
</Danger>

## Instalar el recurso

Hay una versión para **ESX** y otra para **QBCore y Qbox**. Coge la de tu framework.

<Steps>
  <Step title="Descarga Boosting Creator">
    Descarga la versión de tu framework y extrae la carpeta `boosting_creator` en la carpeta `resources` de tu servidor.
  </Step>
  <Step title="Configura el server.cfg">
    Arráncalo **después** de todo lo que necesita, por ejemplo:

    ```cfg
    ensure oxmysql
    ensure ox_lib
    ensure es_extended
    ensure vehicles_keys
    ensure boosting_creator
    ```
  </Step>
  <Step title="Base de datos">
    Nada que hacer: las tablas se crean en el primer arranque y cada actualización añade las columnas nuevas.

    Los archivos de `boosting_creator/sql/` son solo para bases de datos en las que el script no puede crear tablas.
  </Step>
  <Step title="Añade el item del portátil">
    Los jugadores abren el portátil de boosting con un item, por defecto `boosting_laptop`. Mira [Crear el item](#crear-el-item) más abajo.
  </Step>
  <Step title="Da el permiso de admin">
    Mira [Permiso de admin](#permiso-de-admin) más abajo y luego abre el panel con `/boostingcreator`.
  </Step>
</Steps>

## Crear el item

El nombre del item se fija en el panel, **Ajustes > General > Nombre del item del portátil**. Cambiarlo requiere reiniciar el script.

<Tabs>
  <Tab title="jaksam inventory">
    Nada que hacer: el item se crea automáticamente al arrancar, y de nuevo cuando se reinicia el inventario.

    Para la imagen del item, copia `boosting_creator/images/boosting_laptop.png` a `jaksam_inventory_data/_images/`.
  </Tab>
  <Tab title="ox_inventory">
    Añade esto a `ox_inventory/data/items.lua`:

    ```lua
    ['boosting_laptop'] = {
        label = 'Boosting Laptop',
        weight = 1000,
        stack = false,
        close = true,
        description = 'Contracts for those who know where to look',
    },
    ```

    El script escucha el propio evento de uso de ox_inventory, no hace falta `server.export`.

    Para la imagen del item, copia `boosting_creator/images/boosting_laptop.png` a `ox_inventory/web/images/`.
  </Tab>
  <Tab title="ESX">
    Ejecuta esto en tu base de datos:

    ```sql
    INSERT IGNORE INTO `items` (`name`, `label`, `weight`) VALUES ('boosting_laptop', 'Boosting Laptop', 1);
    ```
  </Tab>
  <Tab title="QBCore">
    Añade esto a `qb-core/shared/items.lua`:

    ```lua
    ['boosting_laptop'] = {['name'] = 'boosting_laptop', ['label'] = 'Boosting Laptop', ['weight'] = 1000, ['type'] = 'item', ['image'] = 'boosting_laptop.png', ['unique'] = true, ['useable'] = true, ['shouldClose'] = true, ['combinable'] = nil, ['description'] = 'Contracts for those who know where to look'},
    ```

    Para la imagen del item, copia `boosting_creator/images/boosting_laptop.png` a `qb-inventory/html/images/`.
  </Tab>
</Tabs>

<Info>
  Si el item no existe, la consola del servidor lo indica en amarillo al arrancar: `The item boosting_laptop doesn't exist, create it in your inventory to use the laptop`.
</Info>

## Permiso de admin

El panel y cada acción de admin comprueban un ace, por defecto `boostingcreator` (se puede cambiar en **Ajustes > General**). El ace `jaksam` también funciona siempre.

```cfg
add_ace group.admin boostingcreator allow
```

<Tip>
  Sin el permiso, `/boostingcreator` abre una ventana con las líneas `add_ace` exactas para tu license y tu cuenta de Steam, listas para copiar en el `server.cfg`.
</Tip>

## Verificación

Abre `/boostingcreator` (o `/boostcreator`) en el juego. Si el panel se abre con las clases de la D a la S ya creadas, el script está funcionando correctamente.

Luego date el portátil, úsalo y entra en la cola: con los ajustes por defecto la primera oferta llega entre 45 y 120 segundos después.

## Actualizar

<Warning>
  Antes de actualizar, haz una copia de `boosting_creator/current_config.json` (todos los ajustes del panel) y de la carpeta `boosting_creator/integrations/`, y vuelve a ponerlos en la nueva versión. Si reemplazas la carpeta sin ellos, vuelven los ajustes y las integraciones por defecto.
</Warning>

Las clases, los vehículos, las ubicaciones, los fixers y los perfiles de los jugadores están en la base de datos y se conservan. Consulta también [Cómo actualizar los scripts](/es/jaksams-scripts/how-to-update-the-scripts).
