---
title: "Crear un documento propio"
description: "Añade a Jaksam Identity tu propio documento de identidad, licencia o placa, paso a paso: el item, el tipo de documento, su aspecto, dónde se expide y cómo probarlo."
icon: "pen-ruler"
---

Un documento son dos cosas: **un item en tu inventario** y **una entrada en `Config.Documents`** (`config/documents.lua`). Esta página construye dos ejemplos desde cero:

- una **licencia de caza**, un documento `license` que se expide en una oficina ciudadana
- una **placa de bomberos**, un documento `badge` para el trabajo `fire`

Los mismos pasos sirven para cualquier otra tarjeta. Qué significan los tres tipos en el registro está en [Documentos y registro](/es/jaksam-identity/guides/documents-and-register).

## Elegir el tipo

| Tipo | Para qué | El registro lo da por válido mientras |
| --- | --- | --- |
| `identity` | Documentos de identidad, pasaportes, permisos de residencia | el estado del registro sea válido |
| `license` | Todo lo que se basa en una licencia de tu framework | el estado sea válido **y** el personaje siga teniendo la licencia |
| `badge` | Identificaciones de servicio de un trabajo | el estado sea válido **y** el titular siga teniendo el trabajo |

## Paso a paso

<Steps>
  <Step title="Comprobar que la licencia existe (solo license)">
    <Tabs>
      <Tab title="ESX">
        El tipo de licencia debe ser una fila de la tabla `licenses` de esx_license. Si ningún otro script la añade, añádela tú:

        ```sql
        INSERT INTO licenses (type, label) VALUES ('hunting', 'Hunting licence');
        ```

        Si falta, la consola escribe al arrancar `hunting: licence type "hunting" is not in the licenses table`.
      </Tab>
      <Tab title="QBCore / Qbox">
        No hay nada que crear: la licencia es la clave `hunting` en los metadatos del personaje `licences`. El script conoce todos los tipos de licencia que usa un documento.
      </Tab>
    </Tabs>
  </Step>

  <Step title="Añadir el item">
    El nombre del item es libre, solo tiene que coincidir con `item` en el siguiente paso. Ponle una imagen con el nombre del item (por ejemplo `hunting_license.webp`) en la carpeta de imágenes de tu inventario.

    <Tabs>
      <Tab title="jaksam_inventory">
        Añádelo a `jaksam_inventory_data/items.lua`. `type = 'idcards'` le da las acciones de clic derecho **View**, **Show** y **Copy number**, `onUse` se lo pasa al script y `dynamicMetadata` rellena un documento que viene de una tienda o de un give de admin:

        ```lua
        ['hunting_license'] = {
            label = 'Hunting licence',
            weight = 0.01,
            stackable = false,
            close = true,
            type = 'idcards',
            onUse = function(playerId, inventoryId, slotId)
                TriggerEvent('jksm_identity:use', playerId, inventoryId, slotId)
            end,
            dynamicMetadata = {
                serial = { metadataTemplateId = 'doc_serial', onlyFirstAdd = true },
                firstname = { metadataTemplateId = 'doc_firstname', onlyFirstAdd = true },
                lastname = { metadataTemplateId = 'doc_lastname', onlyFirstAdd = true },
                dob = { metadataTemplateId = 'doc_dob', onlyFirstAdd = true },
                sex = { metadataTemplateId = 'doc_sex', onlyFirstAdd = true },
                issued = { metadataTemplateId = 'doc_issued', onlyFirstAdd = true },
                expires = { metadataTemplateId = 'doc_expires', onlyFirstAdd = true },
            },
            displayFields = {
                { field = 'lastname', label = 'Last name: ${value}' },
                { field = 'firstname', label = 'First name: ${value}' },
                { field = 'serial', label = 'No.: ${value}' },
                { field = 'expires', label = 'Valid until: ${value}' },
            },
        },
        ```

        - Una licencia con **clases** necesita además `classes = { metadataTemplateId = 'doc_classes', onlyFirstAdd = true }`
        - Una **placa** necesita además `rank = { metadataTemplateId = 'doc_rank', onlyFirstAdd = true }`

        Reinicia `jaksam_inventory` una vez.
      </Tab>
      <Tab title="ox_inventory">
        Añádelo a `ox_inventory/data/items.lua`. Los datos de los documentos de tiendas y de gives de admin los pone el script, aquí no hacen falta metadatos:

        ```lua
        ['hunting_license'] = {
            label = 'Hunting licence', weight = 10, stack = false, close = true, consume = 0,
            client = { image = 'hunting_license.webp' },
            server = { export = 'jksm_identity.useDocument' },
            buttons = {
                { label = 'View', action = function(slot) exports.jksm_identity:viewSlot(slot) end },
                { label = 'Show', action = function(slot) exports.jksm_identity:showSlot(slot) end },
            },
        },
        ```
      </Tab>
      <Tab title="qb-inventory">
        Añádelo a `qb-core/shared/items.lua`. El script se encarga de usarlo en cuanto el item está en `Config.Documents`:

        ```lua
        hunting_license = { name = 'hunting_license', label = 'Hunting licence', weight = 10, type = 'item', image = 'hunting_license.webp', unique = true, useable = true, shouldClose = true, description = 'Permit to hunt' },
        ```
      </Tab>
    </Tabs>
  </Step>

  <Step title="Añadir el tipo de documento">
    Una entrada en `Config.Documents`. La clave (`hunting`, `badge_fd`) es el **tipo de documento**: se guarda en el registro y la usan las oficinas, los comandos y los exports. No la renombres cuando ya existan documentos de ese tipo.

    ```lua
    hunting = {
        item = 'hunting_license',
        kind = 'license',
        license = 'hunting',
        label = 'Hunting licence',
        validityDays = 120,
        theme = { header = 'STATE OF SAN ANDREAS', title = 'HUNTING LICENSE', primary = '#2f4a2a', secondary = '#f1efe4', accent = '#c07a2c' },
    },

    badge_fd = {
        item = 'fd_identity',
        kind = 'badge',
        job = 'fire',
        label = 'LSFD badge',
        layout = 'badge',
        theme = { header = 'CITY OF LOS SANTOS', title = 'FIRE DEPARTMENT', word = 'FIRE', emblem = 'shield', primary = '#8a1c12', secondary = '#f5ede6', accent = '#e0a526', authority = 'FIRE CHIEF', authorityName = '' },
    },
    ```

    | Campo | Descripción |
    | --- | --- |
    | `item` | El item del paso anterior |
    | `kind` | `identity`, `license` o `badge` |
    | `license` | (`license`) el tipo de licencia |
    | `licenses` | (`license`, en lugar de `license`) varios tipos de licencia impresos como clases, por ejemplo `{ boat_small = 'A', boat_large = 'B' }` |
    | `job` | (`badge`) el trabajo al que pertenece la placa |
    | `label` | Nombre en los menús y las oficinas. Un texto o una clave de locale con `L('...')` |
    | `validityDays` | Días hasta que caduca, `nil` para nunca |
    | `layout` | `id` (tarjeta horizontal, por defecto) o `badge` (identificación de servicio vertical) |
    | `theme` | El aspecto, ver [El aspecto de la tarjeta](#el-aspecto-de-la-tarjeta) |
  </Step>

  <Step title="Decidir quién lo expide">
    <Tabs>
      <Tab title="identity / license">
        Añade el tipo a los `documents` de una oficina y dale sus tasas en `Config.Offices` (`config/office.lua`), o en la página de oficinas de `/documents config`:

        ```lua
        fees = {
            hunting = { first = 300, renew = 120, replace = 350 },
        },
        locations = {
            { label = 'Ranger station', coords = vec4(0.0, 0.0, 0.0, 0.0), model = 's_m_y_ranger_01', documents = { 'hunting' } },
        },
        ```

        Sin una oficina que lo tenga en su lista, el documento existe pero **ningún mostrador lo entrega**. Una licencia solo se expide a personajes que la tienen: la oficina no la concede.

        Un documento `identity` también puede ir a cada personaje nuevo: añade el tipo a `Config.Starter.documents`. Ver [Oficinas ciudadanas](/es/jaksam-identity/guides/citizen-offices).
      </Tab>
      <Tab title="badge">
        Las placas nunca se expiden en una oficina. Expídelas con el comando de admin, o desde tu propio menú de jefe con el export `Issue`:

        ```lua
        local serial, reason = exports["jksm_identity"]:Issue(employeeId, "badge_fd", { issuerSrc = bossId })
        ```

        El empleado debe tener el trabajo de la placa, si no `reason` es `wrong_job`. Para limitar quién puede expedirla, usa el [hook CanIssue](/es/jaksam-identity/server/hooks/can-issue). Ver [Issue](/es/jaksam-identity/server/register/issue).
      </Tab>
    </Tabs>
  </Step>

  <Step title="Reiniciar y probar">
    Reinicia `jksm_identity` y luego en el juego:

    ```bash
    /documents issue <your id> hunting grant    # grant gives the licence first
    /documents issue <your id> badge_fd force   # force skips the job check
    ```

    Usa el item para mirarlo y compruébalo con `/documents check <serial>`.
  </Step>
</Steps>

## El aspecto de la tarjeta

Todos los campos de `theme` son opcionales.

| Campo | Dónde aparece |
| --- | --- |
| `header` | Línea pequeña arriba. Por defecto `STATE OF SAN ANDREAS` |
| `title` | Título grande en el anverso (en las placas también en el reverso). Por defecto el `label` en mayúsculas |
| `primary` | La banda de color de arriba, la banda de la palabra de las placas y el interior del emblema. También el color del documento en la [cartera del teléfono](/es/jaksam-identity/guides/roadphone-wallet) |
| `secondary` | El fondo de la tarjeta |
| `accent` | La línea bajo la banda de arriba, el anillo del emblema, el número y la fecha de caducidad, el marco de la foto de las placas |
| `emblem` | El sello: `star` (por defecto), `shield`, `starOfLife` o `wrench`. En las placas también la marca de agua del reverso |
| `notice` | El texto del reverso. El de por defecto depende del tipo |
| `word` | (`badge`) la palabra en la banda de abajo, por ejemplo `POLICE` |
| `authority` | (`badge`) el cargo bajo la línea de firma del reverso, por ejemplo `CHIEF OF POLICE` |
| `authorityName` | (`badge`) el nombre que firma en esa línea, vacío para ninguno |

Los colores son valores hex (`#1d4e89`). Usa un `secondary` claro y un `primary` oscuro: los datos se imprimen en texto oscuro sobre el fondo, las bandas llevan texto blanco.

<Tip>
  El rango de una placa es la etiqueta del grado del trabajo que tenía el titular cuando se expidió.
</Tip>

## Falsificarlo

Un documento propio se puede falsificar igual que los que vienen incluidos. A partir de qué nivel de falsificador depende de su tipo, en `Config.Forging.levels` (`config/forgery.lua`): por defecto los documentos de identidad desde el primer nivel, las licencias desde el segundo y las placas desde el cuarto. Ver [Falsificación, trabajadores y pedidos](/es/jaksam-identity/guides/forging).
