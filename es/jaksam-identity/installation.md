---
title: "Instalación"
description: "Instala Jaksam Identity en tu servidor de FiveM con ESX, QBCore o Qbox, añade los items a tu inventario y configura las primeras oficinas y talleres."
icon: "download"
---

Pon **Jaksam Identity** en marcha en tu servidor de FiveM.

## Requisitos

| Recurso | Para qué |
| --- | --- |
| `es_extended` (con las tablas de esx_license) **o** `qb-core` / `qbx_core` | Framework |
| `jaksam_inventory` 1.28 o superior, **o** `ox_inventory`, **o** `qb-inventory` 2.2 (solo versión QBCore) | Los documentos son items con datos |
| `ox_lib`, `oxmysql` | Callbacks, menús, base de datos |
| `ox_target` **o** `qb-target` (solo versión QBCore) | Targets |
| `bob74_ipl` | El interior del taller de falsificación |
| RoadPhone (opcional) | Números de teléfono en las tarjetas de visita, [cartera del móvil](/es/jaksam-identity/guides/roadphone-wallet) |
| `esx_dmvschool` (opcional, solo ESX) | El primer carné de conducir se expide tras el examen de conducir |

<Warning>
  El script crea y actualiza sus propias tablas de la base de datos al arrancar. **Haz una copia de seguridad de tu base de datos** antes de instalar y antes de cada actualización.
</Warning>

## Instalar el recurso

Hay una versión para **ESX** y otra para **QBCore y Qbox** (detecta sola cuál de los dos está en marcha). Coge la de tu framework.

<Tabs>
  <Tab title="ESX" icon="server">
    <Steps>
      <Step title="Descarga Jaksam Identity">
        Descarga la versión ESX y extrae la carpeta `jksm_identity` en la carpeta `resources` de tu servidor.
      </Step>
      <Step title="Configura el server.cfg">
        Arráncalo **después** de todo lo que necesita, por ejemplo:

        ```cfg
        ensure oxmysql
        ensure ox_lib
        ensure es_extended
        ensure jaksam_inventory
        ensure ox_target
        ensure bob74_ipl
        ensure jksm_identity
        ```
      </Step>
      <Step title="Base de datos">
        Nada que hacer: las tablas se crean y se actualizan al arrancar (`jksm_identity_schema` guarda la versión).

        `install/install.sql` es solo para bases de datos en las que el script no puede crear tablas.
      </Step>
      <Step title="Añade los items">
        Añade los items a tu inventario, mira [Instalar los items](#instalar-los-items) más abajo.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge`: inventario (`'jaksam'` o `'ox_inventory'`), notificaciones (`'esx'` o `'ox_lib'`), móvil (`'roadphone'` o `'none'`) y menús
        - `Config.Locale`: `'en'` o `'de'`
        - `Config.AdminGroups` / `Config.AdminAce`: quién puede usar el comando de admin
        - `Config.Debug = false` en un servidor en producción
      </Step>
    </Steps>

    <Warning>
      **esx_dmvschool:** su evento `esx_dmvschool:addLicense` no se comprueba en el servidor, así que un cliente tramposo puede darse cualquier licencia con él. Jaksam Identity confía en las licencias de la base de datos y, con `Config.DmvSchool` activo, expide el carné de conducir tras ese evento. Protege el evento en esx_dmvschool, o pon `Config.DmvSchool.enabled = false`, en un servidor en producción.
    </Warning>
  </Tab>
  <Tab title="QBCore / Qbox" icon="server">
    <Steps>
      <Step title="Descarga Jaksam Identity">
        Descarga la versión QBCore y extrae la carpeta `jksm_identity` en la carpeta `resources` de tu servidor.
      </Step>
      <Step title="Quita qbx_idcard (Qbox)">
        Jaksam Identity ocupa su lugar: responde al nombre `qbx_idcard`, a sus exports `GetMetaLicense` y `CreateMetaLicense` y a su evento de mostrar, así que los items iniciales de qbx_core y qbx_cityhall siguen funcionando sin cambios.

        <Warning>
          Con `qbx_idcard` todavía en marcha, se abrirían dos tarjetas.
        </Warning>
      </Step>
      <Step title="Configura el server.cfg">
        Arráncalo **después** de todo lo que necesita, por ejemplo:

        ```cfg
        ensure oxmysql
        ensure ox_lib
        ensure qb-core
        ensure qb-inventory
        ensure qb-target
        ensure bob74_ipl
        ensure jksm_identity
        ```
      </Step>
      <Step title="Base de datos">
        Nada que hacer: las tablas se crean y se actualizan al arrancar (`jksm_identity_schema` guarda la versión).

        `install/install.sql` es solo para bases de datos en las que el script no puede crear tablas.
      </Step>
      <Step title="Añade los items">
        Añade los items a tu inventario, mira [Instalar los items](#instalar-los-items) más abajo.
      </Step>
      <Step title="config/main.lua">
        - `Config.Bridge.framework = 'auto'` detecta si está en marcha qb-core o qbx_core
        - `Config.Bridge.target = 'auto'` usa ox_target si está instalado, si no qb-target
        - `Config.Bridge.inventory`: `'jaksam'`, `'ox_inventory'` o `'qb-inventory'`
        - `Config.Locale`: `'en'` o `'de'`
        - `Config.AdminGroups` / `Config.AdminAce`: quién puede usar el comando de admin
        - `Config.Debug = false` en un servidor en producción
      </Step>
    </Steps>

    <Info>
      - **Items:** el DNI, el carné de conducir y el permiso de armas son los items propios de QBCore `id_card`, `driver_license` y `weaponlicense`. Las placas, las tarjetas de visita y el material del taller son items de este script.
      - **Items iniciales y ayuntamiento:** lo que entregan qb-core, qbx_core y qb-cityhall / qbx_cityhall se convierte en un documento registrado del personaje. qbx_cityhall lo expide con una foto hecha allí.
      - **Campos antiguos de la tarjeta:** cada tarjeta lleva además `citizenid`, `birthdate`, `nationality` y `cardtype` para los scripts que los leen.
      - **Las licencias** salen de los metadatos del personaje `licences` (`driver` es el `drive` del script).
      - **Dinero negro:** en QBCore el item `markedbills` (su valor en `metadata.worth`), en Qbox el item apilable `black_money`.
      - El soporte de esx_dmvschool solo está en la versión ESX.
    </Info>
  </Tab>
</Tabs>

## Instalar los items

<Tabs>
  <Tab title="jaksam_inventory" icon="boxes-stacked">
    <Steps>
      <Step title="Añade las entradas de los items">
        Añade las entradas de `install/jaksam_items.lua` a `jaksam_inventory_data/items.lua`, dentro de la tabla después de `return { }`.
      </Step>
      <Step title="Añade los tipos de item">
        Copia `install/jaksam_item_types.lua` tal cual a `jaksam_inventory_data/_data/jksm_identity.lua`. Añade las acciones de clic derecho **View**, **Show** y **Copy number**. Nada que pegar: los archivos de esa carpeta sobreviven a las actualizaciones del inventario.
      </Step>
      <Step title="Copia las imágenes">
        Copia `install/images/*.webp` a `jaksam_inventory_data/_images/`.
      </Step>
      <Step title="Reinicia el inventario">
        Reinicia `jaksam_inventory` una vez.
      </Step>
    </Steps>

    Mira [Items de tiendas o de admin](#items-de-tiendas-o-de-admin) para el bloque de metadatos que debe conservar cada item de documento.
  </Tab>
  <Tab title="ox_inventory" icon="box">
    Pon `Config.Bridge.inventory = 'ox_inventory'` y `Config.InventoryKeys = { 'TAB' }` (la tecla que abre el inventario junto a una tarjeta abierta).

    <Steps>
      <Step title="Añade los items">
        Añade `install/ox_items.lua` a `ox_inventory/data/items.lua`.
      </Step>
      <Step title="Copia las imágenes">
        Copia `install/images/*.webp` a `ox_inventory/web/images/`.
      </Step>
    </Steps>

    - Los documentos reciben un export de uso (mostrar o mirar, `Config.UseAction`) y los botones de clic derecho **View** y **Show**. Copiar el número es el propio "Copy serial number" de ox_inventory.
    - **Los documentos de tiendas y de admin** reciben sus datos del script a través del hook `createItem` de ox, sin metadatos en las definiciones de los items.
    - **Los montones de ID** son contenedores de ox, creados por el script. Una cartera solo cuenta para la cartera del móvil si es un contenedor de ox (`setContainerProperties`) incluido en `Config.WalletContainers`. ox no permite un contenedor dentro de otro.
    - **Los documentos en el suelo** los puede ver quien haya abierto ese drop.
  </Tab>
  <Tab title="qb-inventory" icon="box-open">
    Solo versión QBCore, hecha para **qb-inventory 2.2**. Pon `Config.Bridge.inventory = 'qb-inventory'` y `Config.InventoryKeys = { 'TAB' }`.

    <Steps>
      <Step title="Añade los items">
        Añade `install/qb_items.lua` a `qb-core/shared/items.lua`, sustituyendo los tres items de tarjeta que QBCore ya tiene.
      </Step>
      <Step title="Copia las imágenes">
        Copia `install/images/*.webp` a `qb-inventory/html/images/`.
      </Step>
    </Steps>

    No hay que cambiar nada dentro de qb-inventory, y su propio DNI del chat ya no aparece.

    - **Usar un documento** lo muestra o lo abre (`Config.UseAction`). qb-inventory no tiene botones de clic derecho, así que pon `Config.UseAction = 'menu'` para elegir cada vez entre mirar y mostrar. Una tarjeta de visita siempre pregunta (mirar, mostrar, entregar). El número se copia desde la tarjeta abierta.
    - **Los documentos de items iniciales, del ayuntamiento, de una tienda o de `/giveitem`** reciben sus datos del script (hook `ItemAdded` de qb-inventory).
    - **Sin montones de ID:** qb-inventory no tiene contenedores. Los documentos de un pedido llegan uno a uno al almacén de resultados, y la cartera del móvil solo lee el inventario principal.
    - **Un almacén está abierto para un jugador a la vez** (regla de qb-inventory). Lo que los trabajadores meten mientras está abierto se ve al volver a abrirlo.

    <Warning>
      **Documentos sellados:** qb-inventory toma los datos de un item del cliente cuando un jugador lo da o lo tira. Por eso cada documento lleva un sello hecho con una clave que solo conoce el servidor (tabla `jksm_identity_settings`, creada en el primer arranque). Un documento con datos inventados o cambiados no tiene un sello válido: no muestra nada y lo dice. **Conserva esa tabla cuando muevas la base de datos**, o los documentos de los inventarios pierden su sello.
    </Warning>
  </Tab>
</Tabs>

### Items de tiendas o de admin

Cuando el script expide un documento, pasa él mismo los metadatos. Cuando un item de documento aparece de otra forma (una tienda de jaksam, una entrega de admin), lo rellenan las plantillas de metadatos. Las entradas de `install/jaksam_items.lua` ya llevan este bloque, consérvalo en cada item de documento:

```lua
dynamicMetadata = {
    serial    = { metadataTemplateId = 'doc_serial',    onlyFirstAdd = true },
    firstname = { metadataTemplateId = 'doc_firstname', onlyFirstAdd = true },
    lastname  = { metadataTemplateId = 'doc_lastname',  onlyFirstAdd = true },
    dob       = { metadataTemplateId = 'doc_dob',       onlyFirstAdd = true },
    sex       = { metadataTemplateId = 'doc_sex',       onlyFirstAdd = true },
    issued    = { metadataTemplateId = 'doc_issued',    onlyFirstAdd = true },
    expires   = { metadataTemplateId = 'doc_expires',   onlyFirstAdd = true },
    classes   = { metadataTemplateId = 'doc_classes',   onlyFirstAdd = true }, -- only with licence classes
},
```

Las plantillas se registran al arrancar y de nuevo cada vez que jaksam_inventory se reinicia. Un documento creado por una plantilla está **registrado** (real), salvo que su `rarity` de jaksam esté en `Config.UnregisteredRarities` (por defecto `illegal`).

## Configurar

<Steps>
  <Step title="config/documents.lua">
    Los tipos de documento, sus items, validez y temas. Cualquier licencia que conozca tu framework puede ser un documento: añade el item y una entrada aquí. Mira [Documentos y registro](/es/jaksam-identity/guides/documents-and-register).
  </Step>
  <Step title="config/office.lua">
    Los documentos iniciales (`Config.Starter`, por defecto el DNI) y las oficinas ciudadanas (`Config.Offices`): lugares, modelos de NPC, qué documentos gestiona cada oficina, tasas, efectivo o banco. Mira [Oficinas ciudadanas](/es/jaksam-identity/guides/citizen-offices).
  </Step>
  <Step title="config/forgery.lua">
    Pon los talleres de falsificación en `Config.Forgery.workshops` (entrada exterior, precio, los trabajos que pueden tenerlo), o añádelos en el juego con `/documents config`. **De serie no hay ningún taller configurado**: el lado de la falsificación queda invisible hasta que añadas uno. Mira [Talleres de falsificación](/es/jaksam-identity/guides/forgery-workshops).
  </Step>
  <Step title="config/raid.lua">
    Los cuerpos que hacen redadas en los talleres (tus trabajos de policía, desde qué rango) y dónde está el armario de pruebas de cada cuerpo. Sin armario no se puede incautar nada. `Config.Raid.enabled = false` desactiva las redadas. Mira [Redadas](/es/jaksam-identity/guides/raids).
  </Step>
</Steps>

<Tip>
  La mayoría de estos ajustes, lugares incluidos, se pueden cambiar en el juego con `/documents config`, sin editar archivos ni reiniciar. Mira [Ajustes en el juego](/es/jaksam-identity/guides/settings-in-game).
</Tip>

## Verificación

Arranca el servidor y lee la consola. Un recurso que falta o un bridge sin archivo aparece en rojo. **Ninguna línea roja significa que las comprobaciones de arranque han pasado** (con `Config.Debug = true` también imprime `start checks passed`).

En el juego, abre `/documents` como admin: sin subcomando muestra todos los disponibles.
