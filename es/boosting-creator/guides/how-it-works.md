---
title: "Cómo funciona un contrato"
description: "El lado del jugador en Boosting Creator: el portátil, la cola, las ofertas, el robo del auto, el rastreador y las formas en que puede terminar un contrato."
icon: "route"
---

Esta página sigue un contrato desde el portátil hasta el pago, tal como lo ve el jugador.

## El portátil y la cola

El jugador usa el item **portátil de boosting** y pulsa **Entrar en la cola**. La cola sigue activa después de cerrar el portátil: una pequeña etiqueta en pantalla muestra cuánto tiempo lleva esperando.

- Los trabajos de policía no pueden entrar en la cola (mira [Policía](/es/boosting-creator/guides/police)).
- Después de un contrato puede haber una espera antes de la siguiente oferta, y un límite diario por personaje. Los dos se fijan en **Ajustes > Contratos** y se muestran en la misma etiqueta como cuenta atrás.

## La oferta

Cada 45 a 120 segundos (por defecto) un jugador en la cola recibe una oferta de una clase que ha desbloqueado, con suficiente policía conectada y un sitio libre donde crear el auto. Las clases más altas salen más a menudo una vez desbloqueadas.

La oferta muestra la clase, el vehículo, el pago o "El vehículo es tuyo", la reputación que da, el tiempo límite y los riesgos: rastreador, guardias, persecución de banda, dificultad del puente. Es anónima, o un email de un [fixer](/es/boosting-creator/guides/fixers) que puede pedir algo más. El jugador acepta o rechaza en menos de 60 segundos.

Si el portátil está cerrado, la oferta llega como notificación con un sonido de teléfono.

<Frame>
  ![Portátil de boosting con una oferta de contrato](/images/boosting-creator/laptop-offer.jpg)
</Frame>

## Encontrar el auto

En el mapa aparece un círculo amarillo. El auto está en algún punto dentro de él, nunca en el centro, y el círculo se encoge a su alrededor a medida que el jugador se acerca. El auto solo se crea cuando hay alguien cerca, cerrado y con su propia matrícula. Puede haber guardias armados a su alrededor.

<Frame>
  ![Tarjeta de objetivo de un contrato activo](/images/boosting-creator/objective-card.jpg)
</Frame>

## Robarlo

<Tabs>
  <Tab title="Sin vehicles_keys">
    1. **Forzar**: a pie junto al auto, pulsa **E** y supera el skill check. Cada intento hace saltar la alarma y alerta a los guardias.
    2. **Puente**: en el asiento del conductor pulsa **H** y juega al minijuego del puente (por defecto, conectar los cables de colores). Fácil, Media o Difícil depende de la clase. Un error provoca chispas, una breve espera y la alarma.
  </Tab>
  <Tab title="Con vehicles_keys">
    El jugador usa la ganzúa o rompe el cristal y hace el puente con vehicles_keys, como con cualquier otro auto. El auto robado recibe llaves temporales, que se quitan al final del contrato.
  </Tab>
</Tabs>

Al forzar el auto alguien puede **verte**: según la clase, un testigo llama a la policía unos segundos después. La tarjeta del objetivo lo indica.

## La huida

Una vez robado el auto:

- **Rastreador GPS** (clases que lo tienen): la policía ve un círculo alrededor del auto cada pocos segundos. Los pasajeros, o el conductor con el auto parado, lo hackean con **J**, varias veces seguidas. Cuando el último hackeo sale bien, se pierde la señal.
- **Persecución de banda** (clases que la tienen): detrás del ladrón aparecen autos con pistoleros. Termina cuando los destruyen, los dejan atrás o pasados unos minutos.

La entrega solo se muestra cuando el rastreador ya no está.

## El final del contrato

| Final | Qué pasa |
| --- | --- |
| **Entrega** | Para dentro del marcador verde y pulsa **E**. Un comprador va hasta el auto, se sube y se va. El pago baja con los daños del auto. |
| **VIN scratch** | En un taller de carrocería, a pie, pulsa **E**: tras 10 segundos el auto es del jugador, guardado en su garaje. Sin dinero. |
| **Desguace** | Desmonta las puertas, el capó, el maletero y las ruedas una a una y lleva cada pieza al punto de entrega. Cada pieza paga su parte al momento. |
| **Garaje propio** | En un contrato de entrega simple, el auto se puede guardar en el [garaje](/es/boosting-creator/guides/garages-and-car-carrier) del jugador para venderlo más tarde. |

Un contrato **falla** cuando se acaba el tiempo, el jugador muere, el auto queda destruido o desaparece, o el jugador lo abandona desde el portátil. Un contrato fallido o caducado quita algo de reputación.

## Reputación

Cada clase da reputación cuando se completa el trabajo. La reputación desbloquea las clases siguientes y sube el nivel que se muestra en el portátil. El portátil también guarda el historial de los últimos contratos y el total ganado.
