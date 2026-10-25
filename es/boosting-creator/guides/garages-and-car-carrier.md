---
title: "Garajes y portavehículos"
description: "Los garajes de Boosting Creator: compra uno, guarda autos robados en 6 plazas, sácalos para venderlos o vende todo el garaje en un portavehículos que la policía puede incautar."
icon: "warehouse"
---

Los ladrones pueden comprar un **garaje** y quedarse los autos robados en lugar de venderlos al momento. Más tarde los sacan de uno en uno, o los cargan todos en un **portavehículos** para cobrar más. Las dos cosas están activadas por defecto, en **Ajustes > Contratos**, secciones **Garajes** y **Venta al por mayor**.

## Comprar un garaje

Los garajes son [ubicaciones](/es/boosting-creator/guides/locations#garajes) con un precio. La pestaña **Garaje** del portátil muestra los que están en venta, con un botón de waypoint.

En la entrada, a pie, un panel muestra el nombre, la zona, el precio y las 6 plazas. Pulsa **E** dos veces en menos de 3 segundos para comprarlo. El dinero sale de la cuenta fijada en **Cuenta con la que se pagan los garajes**.

Cada personaje tiene un solo garaje. Muchos jugadores pueden comprar el mismo garaje: cada uno entra en su propia copia privada del interior, con sus propios 6 autos.

<Frame>
  ![Panel de la entrada del garaje con el precio](/images/boosting-creator/garage-entrance.jpg)
</Frame>

## Guardar un auto

En un contrato de entrega simple (sin petición de un fixer, ni VIN scratch ni desguace), una vez robado el auto el objetivo dice **o guárdalo en tu garaje**. Para dentro del radio de la entrada y pulsa **E**.

El auto se guarda con su valor: el pago del contrato por el estado del auto. El jugador recibe la reputación de la clase, pero todavía no el dinero. Con el garaje lleno (6 autos) no se ofrece.

## Dentro del garaje

Pulsa **E** en la entrada para entrar a pie. Los autos guardados están en sus plazas, y el panel muestra cada uno con su clase y su valor.

Para **sacar uno**, pulsa **E** a su lado. El auto aparece en la **Salida del auto** del garaje con el ladrón al volante, y empieza al momento una entrega a un comprador libre: ya robado, sin rastreador, sin guardias, sin persecución, y paga el valor guardado por el estado en la entrega. La plaza queda libre sea cual sea el resultado.

## Venta al por mayor

Con al menos **3 autos** (por defecto) el panel interior muestra dos totales: uno a uno, y en el portavehículos con un multiplicador, desde x1,3 con los autos mínimos hasta x2 con el garaje lleno. Pulsa **G** dos veces en menos de 3 segundos para empezar.

- Un camión con su remolque aparece en la **Salida del portavehículos** del garaje, enganchado y con los autos encima, con el ladrón al volante.
- El comprador es un **Comprador al por mayor** a al menos 2.500 m del garaje.
- Necesita **2 policías de servicio** (por defecto) y tiene un límite de 30 minutos.
- El remolque debe seguir enganchado: si se queda más de 150 m atrás durante un minuto, la venta falla.

### Control policial

A los 20 segundos la policía recibe un círculo alrededor del portavehículos, que se mueve cada 40 segundos. Si el camión está parado, el círculo se encoge en cada actualización.

Un agente que se sube al asiento del conductor **incauta** el portavehículos: la venta falla y el agente recibe una ruta al **Depósito** más cercano. Al parar allí se paga a la cuenta de la sociedad una recompensa fija más una parte del valor de la carga, y un bonus opcional al agente.

### Plan B

Parado, a pie al final de la rampa, el ladrón pulsa **E**: el último auto de la carga baja rodando y se convierte en su propia entrega por su valor guardado. El resto de la carga se pierde.
