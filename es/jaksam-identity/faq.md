---
title: "FAQ"
description: "Preguntas frecuentes específicas de Jaksam Identity, sobre talleres, redadas, documentos, sellos de qb-inventory e integraciones."
icon: "circle-question"
---

Esta página contiene FAQs relacionadas **ÚNICAMENTE con este script**. Asegúrate de revisar también la [FAQ común](/es/jaksams-scripts/common-faq) para otros problemas.

<AccordionGroup>
  <Accordion title="No encuentro ningún taller de falsificación en el mundo">
    De serie no hay ningún taller configurado, así que todo el lado de la falsificación queda invisible hasta que añadas uno.

    Añádelos en `Config.Forgery.workshops` (`config/forgery.lua`), o en el juego en la página de talleres de `/documents config`. Mira [Talleres de falsificación](/es/jaksam-identity/guides/forgery-workshops).
  </Accordion>

  <Accordion title="El interior del taller está vacío o es invisible">
    El taller usa el interior de DNI falsos de los bikers de `bob74_ipl`. Asegúrate de que `bob74_ipl` está instalado y arranca **antes** que `jksm_identity`. Si falta, la consola lo indica en rojo al arrancar.
  </Accordion>

  <Accordion title="Los agentes no pueden incautar nada durante una redada">
    Cada cuerpo necesita un armario de pruebas. Colócalo en la página de redadas de `/documents config`, o pon `locker` en `Config.Raid.forces`. Sin armario no se puede incautar nada.
  </Accordion>

  <Accordion title="Los agentes o los invitados dentro de un taller no ven las estaciones">
    Es así a propósito. Solo los miembros del trabajo propietario ven y usan las estaciones, ordenadores y portátiles. Los agentes tienen sus propias opciones durante una redada: incautar en las estanterías y en el portátil del jefe, precintar en la puerta.
  </Accordion>

  <Accordion title="Se abren dos DNI a la vez (Qbox)">
    `qbx_idcard` sigue en marcha. Quítalo: Jaksam Identity responde en su lugar, así que los items iniciales de qbx_core y qbx_cityhall siguen funcionando sin cambios.
  </Accordion>

  <Accordion title="Faltan las acciones de clic derecho View, Show y Copy number (jaksam_inventory)">
    Copia `install/jaksam_item_types.lua` a `jaksam_inventory_data/_data/jksm_identity.lua` y reinicia `jaksam_inventory` una vez. Mira [Instalación](/es/jaksam-identity/installation#instalar-los-items).
  </Accordion>

  <Accordion title="Los documentos no muestran nada y dicen que el sello no es válido (qb-inventory)">
    qb-inventory toma los datos de un item del cliente, así que cada documento lleva un sello hecho con una clave que solo conoce el servidor, guardada en la tabla `jksm_identity_settings`.

    Si moviste o reiniciaste la base de datos sin esa tabla, la clave cambió y los documentos existentes perdieron su sello. Restaura la tabla desde tu copia de seguridad o vuelve a expedir los documentos.
  </Accordion>

  <Accordion title="El DNI inicial no tiene foto">
    Es así a propósito. Los documentos iniciales se expiden justo después de cargar el personaje, sin foto. La foto se hace en una [oficina ciudadana](/es/jaksam-identity/guides/citizen-offices) con una renovación.
  </Accordion>

  <Accordion title="Los documentos comprados en una tienda se detectan como falsos">
    Un documento de una tienda o de una entrega de admin está registrado (real), salvo que su `rarity` de jaksam esté en `Config.UnregisteredRarities` (por defecto `illegal`). Cambia la rareza del item o quita esa rareza de la lista.
  </Accordion>

  <Accordion title="Los documentos caducados o suspendidos se pueden seguir usando">
    Es así a propósito: **hechos, no fuerza**. La caducidad, las suspensiones y las fotos antiguas se muestran en la tarjeta y en la consulta del registro, pero nada se quita, bloquea o renueva automáticamente. Lo que sigue es roleplay.
  </Accordion>

  <Accordion title="¿Puede la policía averiguar quién hizo una falsificación?">
    No. La consulta del registro solo muestra lo que sabría una autoridad: sin registro, estado, caducidad, licencias que faltan, datos que no coinciden. Quién la hizo y su calidad solo lo ven los admins con `/documents truth <serial>`. Quién presentó realmente un documento se escribe en `jksm_identity_log`, solo para admins.
  </Accordion>

  <Accordion title="¿Cómo añado otro documento o licencia?">
    Añade el item a tu inventario y luego una entrada en `Config.Documents` (`config/documents.lua`). Cualquier licencia que conozca tu framework puede ser un documento. Mira [Crear tu propio documento](/es/jaksam-identity/guides/documents-and-register#crear-tu-propio-documento).
  </Accordion>

  <Accordion title="¿Cómo cambio el idioma o añado uno nuevo?">
    `Config.Locale` elige el idioma (vienen `en` y `de`), y los admins lo pueden cambiar en el juego en `/documents config`. Para añadir un idioma, copia `locales/en.lua` a `locales/<code>.lua`, cambia `Locales['en']` por `Locales['<code>']`, traduce los textos y pon el código en `Config.Locale`. Las claves que falten usan el inglés.
  </Accordion>

  <Accordion title="¿Cómo uso mis propias notificaciones, progress bar o minijuego?">
    - Notificaciones: `bridge/notify.lua`, mira [Notificaciones](/es/jaksam-identity/client/replace-notifications)
    - Progress bar: `Editable.Progress` en `editable/client.lua`, mira [Progress bar](/es/jaksam-identity/client/progress-bar)
    - Minijuego: `Editable.SkillCheck` en `editable/client.lua`, mira [Skill check](/es/jaksam-identity/client/skill-check)
  </Accordion>

  <Accordion title="¿Es seguro usar esx_dmvschool con este script?">
    El evento `esx_dmvschool:addLicense` de esx_dmvschool no se comprueba en el servidor, así que un cliente tramposo puede darse cualquier licencia con él. Jaksam Identity confía en las licencias de la base de datos. Protege ese evento en esx_dmvschool, o pon `Config.DmvSchool.enabled = false`, en un servidor en producción.
  </Accordion>
</AccordionGroup>
