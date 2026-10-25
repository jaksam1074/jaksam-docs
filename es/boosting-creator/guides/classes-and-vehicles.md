---
title: "Clases y vehículos"
description: "Crea y ajusta las clases de Boosting Creator: reputación, pago, tiempo límite, policía, rastreador, guardias, persecución de banda, dificultad del puente, VIN scratch y desguace."
icon: "ranking-star"
---

Una **clase** es un nivel de contratos. Con el script vienen cinco, D, C, B, A y S, y puedes editarlas o añadir las tuyas en la pestaña **Clases** de `/boostingcreator`.

## Ajustes de la clase

| Campo | Qué hace |
| --- | --- |
| **ID** | Código corto que se muestra en la etiqueta de la clase. No se puede cambiar después de crear la clase. |
| **Nombre que ven los jugadores** y **Color** | Cómo se ve la clase en el portátil, en el HUD y en el panel. |
| **Reputación para desbloquearla** | Un jugador recibe ofertas de esta clase solo a partir de esta reputación. |
| **Reputación por un contrato completado** | Se da cuando el contrato se completa (entregado, con el VIN borrado o guardado). |
| **Pago mínimo / Pago máximo** | El pago de la oferta es aleatorio entre los dos. |
| **Tiempo límite** | Minutos para terminar el trabajo, de 5 a 240. |
| **Policías de servicio necesarios** | Las ofertas de esta clase solo llegan con al menos estos agentes conectados. |
| **Aviso a la policía al forzar** | Probabilidad de que un testigo llame a la policía cuando se fuerza el auto. |
| **Rastreador GPS** | Activado o desactivado, y cuántos hackeos con éxito lo quitan (de 1 a 10). |
| **Guardias** | De 1 a 6 guardias armados alrededor del auto aparcado, dificultad de 1 a 5. |
| **Persecución de banda** | De 1 a 3 autos perseguidores, de 1 a 3 pistoleros además del conductor, dificultad de 1 a 5. |
| **Puente** | Fácil, Media o Difícil. Solo se usa sin vehicles_keys. |
| **Puede ser un contrato VIN scratch** | La clase puede salir como contrato VIN scratch (cuando el VIN scratch está activado en los ajustes). |
| **Puede ser un contrato de desguace** | La clase puede salir como contrato de desguace (cuando el desguace está activado en los ajustes). |

<Info>
  Al borrar una clase también se quita de los fixers y de las ubicaciones que la usaban. Los autos de esa clase que ya están guardados en un garaje se siguen vendiendo.
</Info>

## Las clases por defecto

| Clase | Reputación | Riesgos |
| --- | --- | --- |
| D | 0 | ninguno, desguace permitido |
| C | 60 | desguace permitido |
| B | 200 | rastreador, desguace permitido |
| A | 500 | rastreador, guardias, VIN scratch permitido |
| S | 1000 | rastreador, guardias, persecución de banda, VIN scratch permitido |

## Vehículos

La pestaña **Vehículos** muestra los autos de cada clase. Una clase puede tener hasta 60 vehículos, y cada oferta elige uno al azar.

- **Añadir vehículos** abre un selector con todos los autos vanilla y su imagen.
- **Añadir por nombre de modelo** añade un auto addon por su nombre de spawn. Para darle una imagen, pon un archivo `<nombre de spawn>.webp` en `boosting_creator/_vehicles_images/`, con el nombre escrito igual que al añadirlo, y reinicia el script.

<Tip>
  Una clase sin vehículos nunca se ofrece. Lo mismo pasa con una clase sin zona de búsqueda o entrega libre: mira [Ubicaciones](/es/boosting-creator/guides/locations).
</Tip>
