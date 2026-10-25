---
title: "Módulos"
description: "Sustituye funciones por defecto de Boosting Creator como el dispatch, las llaves de vehículos, las notificaciones, el text UI, la barra de progreso y el skill check por tus propios módulos."
icon: "puzzle-piece"
---

Los módulos son una forma sencilla de que Boosting Creator funcione con los demás scripts de tu servidor: dispatch, llaves de vehículos, notificaciones y más.

Para elegir un módulo existente, abre el menú `/boostingcreator`, ve a **Ajustes > Módulos** y selecciónalo. Así de fácil.

### Módulos disponibles

| Categoría | Opciones disponibles |
| --- | --- |
| Dispatch | `codesign`, `default`, `rcore`, `roadphone` |
| Keys | `none`, `qb-vehiclekeys`, `vehicles_keys` |
| Logs | `jaksam` |
| Notify | `default`, `ox_lib` |
| Progress Bar | `jaksam`, `ox_lib` |
| Skill Check | `jaksam`, `ox_lib` |
| Text UI | `esx`, `none`, `ox_lib` |

<Info>
  **Keys** (**Llaves de vehículos** en los ajustes) da al ladrón llaves temporales del auto robado y se las quita cuando termina el contrato. Con `vehicles_keys` en marcha, además el auto se abre con ganzúa y se le hace el puente con vehicles_keys en lugar del forzado y el puente propios del script.
</Info>

### Crear un módulo personalizado

<Steps>
  <Step title="Ve a la carpeta de módulos">
    Ve a la carpeta `boosting_creator/_modules/<category>`, por ejemplo `_modules/dispatch`.
  </Step>
  <Step title="Duplica un módulo existente">
    Copia un módulo existente (por ejemplo `default`) y pégalo en la misma carpeta como plantilla.
  </Step>
  <Step title="Renombra la copia">
    Renombra la carpeta y el `moduleName` dentro de sus archivos para que coincidan con el script que estás integrando.
  </Step>
  <Step title="Implementa las funciones">
    Edita las funciones para que llamen a tu script. Para un dispatch:

    ```lua
    local moduleType = "dispatch"
    local moduleName = "yourModuleName"

    -- Don't touch, required to appear in the in-game settings
    Integrations.modules = Integrations.modules or {}
    Integrations.modules[moduleType] = Integrations.modules[moduleType] or {}
    Integrations[moduleType] = Integrations[moduleType] or {}
    Integrations[moduleType][moduleName] = {}
    table.insert(Integrations.modules[moduleType], moduleName)

    -- Server side, once per alert
    Integrations[moduleType][moduleName].alertPoliceServerSide = function(coords, message, category)
        if not IsDuplicityVersion() then return end

        -- Call your dispatch script's export or event here
    end
    ```

    Las funciones que necesita cada categoría:

    | Categoría | Funciones |
    | --- | --- |
    | Dispatch | `alertPoliceServerSide`, `alertPoliceMemberClientSide` |
    | Keys | `giveKeys`, `removeKeys` |
  </Step>
  <Step title="Reinicia y elígelo">
    Reinicia el script y luego elige tu módulo en **Ajustes > Módulos**.
  </Step>
</Steps>
