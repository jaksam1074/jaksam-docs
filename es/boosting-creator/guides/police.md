---
title: "Policía"
description: "Lo que ve y hace la policía en Boosting Creator: avisos al forzar, avisos del rastreador GPS, módulos de dispatch, policía mínima por clase e incautación de portavehículos."
icon: "shield-halved"
---

## Trabajos de policía

Los trabajos que cuentan como policía están en `integrations/sh_integrations.lua`:

```lua
POLICE_JOBS_NAMES = {
    ["police"] = true,
    ["sheriff"] = true,
}
```

Los jugadores con estos trabajos:

- reciben los avisos del rastreador y los avisos al forzar
- cuentan para la **policía mínima** de cada clase y del portavehículos
- no pueden entrar en la cola de boosting
- pueden incautar un portavehículos y llevarlo a un depósito

## Avisos al forzar

Cuando se fuerza el auto de un contrato, el **Aviso a la policía al forzar** de la clase decide si un testigo llama a la policía. El aviso llega a los 10 segundos (por defecto, **Ajustes > Contratos > Aviso a la policía al forzar > Ventaja antes del aviso**) a través del [módulo de dispatch](/es/boosting-creator/modules). Se tira una vez por contrato, y también funciona en las clases sin rastreador.

## Rastreador GPS

En las clases con rastreador, una vez robado el auto cada agente ve un círculo rojo con un blip **Rastreador \<matrícula\>** cada 6 segundos, con un pitido. El primer aviso también indica el modelo y la matrícula.

Los ladrones hackean el rastreador con **J** (se puede cambiar en las asignaciones de teclas de FiveM como "Boosting: hackear el rastreador"). Los pasajeros pueden hackear siempre, el conductor solo con el auto parado. Cada hackeo con éxito agranda el círculo, cada fallo envía un aviso al momento. Cuando el último hackeo sale bien, los agentes ven **Señal del rastreador perdida**.

| Ajuste (**Ajustes > Rastreador**) | Por defecto |
| --- | --- |
| Segundos entre dos avisos a la policía | 6 |
| Segundos entre dos hackeos | 8 |
| Crecimiento del círculo de aviso por hackeo | 60 m |
| El conductor puede hackear con el vehículo parado | activado |

Con un módulo de dispatch distinto de `default`, tu dispatch también recibe un aviso cuando empieza el rastreo.

## Portavehículos

Mira [Garajes y portavehículos](/es/boosting-creator/guides/garages-and-car-carrier#control-policial): un círculo que sigue al portavehículos, la incautación al subirse al asiento del conductor y la recompensa en el depósito.
