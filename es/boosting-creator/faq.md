---
title: "FAQ"
description: "Preguntas frecuentes específicas de Boosting Creator: ofertas que nunca llegan, autos que no aparecen, el item del portátil, rastreadores, vehicles_keys y garajes."
icon: "circle-question"
---

Esta página contiene FAQs relacionadas **ÚNICAMENTE con este script**. Asegúrate de revisar también la [FAQ común](/es/jaksams-scripts/common-faq) para otros problemas.

<AccordionGroup>
  <Accordion title="Estoy en la cola pero nunca llega ninguna oferta">
    Una oferta necesita una clase que el jugador haya desbloqueado y que además tenga:

    - al menos un vehículo
    - suficiente policía conectada (los **Policías de servicio necesarios** de la clase)
    - una zona de búsqueda libre y una entrega libre para esa clase

    Con los valores por defecto la primera oferta llega entre 45 y 120 segundos después. Revisa la pestaña **En vivo**: un jugador en cooldown o en el límite diario aparece en **Jugadores esperando su próximo contrato**.
  </Accordion>

  <Accordion title="El contrato se cancela cuando me acerco al auto">
    El auto lo crea el juego del jugador y lo comprueba el servidor. Si la consola del servidor dice `wasn't created, is the model valid?`:

    - el modelo de la clase está mal, o un auto addon no está en stream
    - `sv_entityLockdown` está en `strict`, así que los jugadores no pueden crear entidades
  </Accordion>

  <Accordion title="Usar el portátil no hace nada">
    Probablemente el item no existe en tu inventario: la consola del servidor lo indica al arrancar, en amarillo. Créalo como se explica en [Crear el item](/es/boosting-creator/installation#crear-el-item). Si cambiaste el nombre del item en los ajustes, reinicia el script.
  </Accordion>

  <Accordion title="Los policías no pueden entrar en la cola">
    Es así a propósito: los trabajos de `POLICE_JOBS_NAMES` no pueden hacer boosting. Mira [Policía](/es/boosting-creator/guides/police).
  </Accordion>

  <Accordion title="La policía no ve el rastreador">
    Los avisos solo llegan a los trabajos de `POLICE_JOBS_NAMES` (`integrations/sh_integrations.lua`). Añade ahí los nombres de tus trabajos de policía y reinicia el script.
  </Accordion>

  <Accordion title="No aparecen los minijuegos de forzar y de hacer el puente">
    Con `vehicles_keys` iniciado, el auto se abre con ganzúa y se le hace el puente con vehicles_keys, y no se usan el forzado ni el puente propios del script. Es así a propósito.
  </Accordion>

  <Accordion title="¿Por qué no puedo guardar este auto en mi garaje?">
    Solo se pueden guardar los contratos de entrega simples: no los de VIN scratch ni los de desguace, no los autos para los que un fixer pidió algo, y no cuando el garaje ya tiene 6 autos.
  </Accordion>

  <Accordion title="El portavehículos no puede salir">
    El panel dentro del garaje dice por qué. Necesita al menos los autos fijados en **Autos necesarios para vender todo**, suficientes policías de servicio y un comprador al por mayor libre a al menos 2.500 m del garaje (por defecto).
  </Accordion>

  <Accordion title="No puedo borrar un garaje">
    Es propiedad de algunos jugadores. Quítaselo primero a cada uno de ellos en la pestaña **Jugadores**.
  </Accordion>

  <Accordion title="La entrega se rechazó por ser demasiado rápida">
    Un auto que llega más rápido de lo que permite cualquier trayecto real (por ejemplo tras un teletransporte) se rechaza, y el intento queda registrado en Discord.
  </Accordion>
</AccordionGroup>
