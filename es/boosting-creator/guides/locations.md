---
title: "Ubicaciones"
description: "Todos los tipos de ubicación de Boosting Creator: zonas de búsqueda, entregas, talleres VIN, desguaces, garajes con su salida del auto y su salida del portavehículos, compradores al por mayor y depósitos."
icon: "location-dot"
---

Todos los lugares del script se configuran en la pestaña **Ubicaciones** de `/boostingcreator`. Cada uno tiene un nombre, una posición con orientación y un radio. **Mi posición** los rellena desde donde estás, o desde el vehículo en el que vas sentado, a nivel del suelo.

Desde el menú de la fila puedes usar **Teletransportarse**, **Marcar waypoint** o, en una zona de búsqueda, **Previsualizar un vehículo aparcado** (aparece un auto transparente en el sitio durante 15 segundos).

## Tipos de ubicación

| Tipo | Qué es | Radio |
| --- | --- | --- |
| **Zona de búsqueda** | Donde está aparcado el auto del contrato. La posición es la plaza de aparcamiento exacta, el radio es el círculo en el que busca el jugador. | De 30 a 500 m |
| **Entrega** | El comprador. El auto tiene que pararse dentro del radio. | De 2 a 20 m |
| **Taller VIN** | Adonde lleva el auto un contrato VIN scratch. | De 2 a 20 m |
| **Desguace** | Adonde lleva el auto un contrato de desguace. Tiene un segundo punto, el **Punto de entrega de piezas**, adonde el ladrón lleva cada pieza. | De 2 a 20 m |
| **Garaje** | Un garaje que los ladrones pueden comprar. Mira [más abajo](#garajes). | De 2 a 20 m |
| **Comprador al por mayor** | Se queda todo un [portavehículos](/es/boosting-creator/guides/garages-and-car-carrier#venta-al-por-mayor). Necesita espacio abierto para un camión con su remolque. | De 2 a 20 m |
| **Depósito** | Adonde los agentes llevan un portavehículos incautado. | De 2 a 20 m |

Las zonas de búsqueda, las entregas, los talleres VIN y los desguaces se pueden limitar a algunas **clases**. Si no hay ninguna seleccionada, valen todas las clases.

<Tip>
  Coloca una zona de búsqueda con un auto de verdad: siéntate en él, aparcado dentro de las líneas y mirando hacia donde debe mirar, y pulsa **Mi posición**. El auto del contrato aparece exactamente ahí.
</Tip>

## Un contrato por sitio

Una oferta reserva su zona de búsqueda y su entrega hasta que termina el contrato, así que dos jugadores nunca reciben el mismo auto o el mismo comprador a la vez. Con muchos jugadores haciendo boosting al mismo tiempo, añade más ubicaciones: una clase sin zona de búsqueda o entrega libre simplemente no se ofrece.

## Garajes

Un garaje tiene tres puntos:

| Punto | Dónde ponerlo |
| --- | --- |
| **Entrada** | A pie en la puerta del garaje. Aquí los jugadores compran el garaje y entran, y paran un auto dentro de su radio para guardarlo. |
| **Salida del auto** | Donde aparece un auto sacado del garaje, con el ladrón al volante. Siéntate en un auto aparcado ahí y pulsa **Mi posición**. |
| **Salida del portavehículos** | Donde aparece el camión cuando se vende todo el garaje. El remolque aparece 11 m justo detrás, así que deja sitio. Siéntate en un vehículo ahí, mirando hacia la carretera, y pulsa **Mi posición**. |

Un garaje también tiene un **Precio**. No usa clases: cualquier ladrón puede comprarlo.

<Warning>
  Un garaje que algunos jugadores ya compraron no se puede borrar. Quítaselo primero a ellos, en la pestaña **Jugadores**.
</Warning>

<Frame>
  ![Ubicación de garaje con entrada, salida del auto y salida del portavehículos](/images/boosting-creator/panel-garage.jpg)
</Frame>

## Las ubicaciones por defecto

El script viene con 10 zonas de búsqueda, 5 entregas, 1 desguace, 1 taller VIN, 6 garajes (Vespucci Beach, LSIA, Elysian Island, Sandy Shores, Grapeseed, Paleto Bay), 4 compradores al por mayor y 1 depósito. Se añaden una sola vez: si los borras, no vuelven.
