---
title: "Crews"
description: "Haz boosting en crew con Boosting Creator: el líder invita desde el portátil a los jugadores cercanos, la crew comparte cada contrato y el pago se reparte con un bonus."
icon: "users"
---

Los jugadores pueden hacer boosting juntos. Una **crew** es un líder y los jugadores que aceptaron su invitación: entra en la cola como uno solo y comparte cada contrato que acepta el líder.

## Formar una crew

1. El líder abre el portátil y va a la pestaña **Crew**. Los jugadores a menos de 10 m aparecen en la lista.
2. El líder los invita. La invitación dura 60 segundos.
3. El jugador invitado acepta desde su propio portátil. A partir de ahí el líder hace cola por él.

El líder no puede invitar mientras hay un contrato en curso. La crew termina cuando el líder la disuelve o se va.

## Durante un contrato

Cualquier miembro puede robar el auto, conducirlo, hackear el rastreador, entregarlo y desmontarlo en un desguace. La tarjeta del objetivo y el mapa son los mismos para todos.

Las ofertas siguen la reputación del líder.

Con **Crews más grandes, más peligro** activado, una crew más grande se enfrenta a más: un guardia más por cada miembro después del primero (hasta 6), y un auto perseguidor más a partir de 3 miembros (hasta 3), en las clases que los tienen.

## Pago y reputación

El pago crece con la crew y se reparte a partes iguales:

```text
total = pay × (1 + bonus % × (members − 1))
share = total ÷ members
```

Con el bonus por defecto del 50 %, un contrato de 10.000 hecho por 2 jugadores paga 15.000 en total, 7.500 cada uno. La oferta muestra la parte de cada miembro.

Cada miembro recibe la reputación de la clase, el contrato en su historial y su propia espera antes del siguiente contrato.

## Ajustes

En **Ajustes > Contratos**, sección **Crew**:

| Ajuste | Por defecto |
| --- | --- |
| Crews | activado. Desactivado, el portátil no tiene la pestaña Crew y cada uno roba solo |
| Crew más grande, líder incluido | 4 jugadores (de 2 a 4) |
| Pago extra por miembro después del primero | 50 % |
| Crews más grandes, más peligro | activado |

La pestaña **En vivo** del panel muestra los miembros de cada contrato en crew.
