---
title: "Fixers"
description: "Los fixers de Boosting Creator: compradores con nombre que envían contratos por email, piden un auto sin un rasguño, repintado o tuneado, y pagan más cuanto más confían en el ladrón."
icon: "envelope"
---

Un **fixer** es un comprador con nombre. En lugar de una oferta anónima, el jugador recibe un email suyo en el portátil, y después del trabajo una respuesta en la **Bandeja de entrada**. Los fixers están activados por defecto y se configuran en la pestaña **Fixers** de `/boostingcreator`.

## Ajustes del fixer

| Campo | Qué hace |
| --- | --- |
| **Nombre que ven los ladrones**, **Iniciales**, color | Cómo aparece el fixer en los emails. |
| **Clases que compran** | Las clases que compra el fixer. |
| **Reputación antes de que escriba a un ladrón** | El fixer solo escribe a los jugadores con esta reputación. |
| **Probabilidad de petición** | Con qué frecuencia el fixer pide algo más. |
| **Peticiones** | Hasta 10, mira más abajo. |
| **Mensajes** | El email de la oferta, y las respuestas cuando el trabajo salió bien, cuando no se cumplió una petición y cuando falló. |

Los mensajes pueden usar `{model}`, `{class}`, `{pay}`, `{colour}`, `{mods}`, `{condition}` y `{amount}`.

## Peticiones

Una petición es un encargo extra en un contrato de entrega:

| Tipo | El auto debe |
| --- | --- |
| **Sin un rasguño** | Llegar con al menos un estado dado, por ejemplo 95 %. |
| **Repintado** | Llegar en uno de los colores elegidos. Aparece en un color muy distinto, así que hay que pintarlo. |
| **Tuning de mecánico** | Tener un número de mejoras entre motor, frenos y transmisión de nivel 2 o superior, turbo y xenón. |

Cada petición tiene un **bonus** si se cumple, una **penalización** si no se cumple, **minutos extra** en el tiempo límite, la **confianza** que necesita y el número de **mecánicos** que deben estar conectados (trabajos fijados en **Ajustes > Contratos**). Mientras conduce, la tarjeta del objetivo muestra cuánto le falta al auto para cumplir la petición, y se pone verde cuando se cumple.

## Confianza

Cada personaje tiene un nivel de confianza de 0 a 100 con cada fixer. Más confianza sube el pago, hasta un +20 % con la confianza máxima por defecto, y desbloquea las peticiones que la necesitan.

- Un trabajo hecho (con la petición cumplida, o sin petición) suma confianza.
- Una petición no cumplida quita algo de confianza.
- Un contrato fallido o caducado quita más.

Las cantidades se fijan en **Ajustes > Contratos**.

## Los fixers por defecto

| Fixer | Compra | Desde reputación | Pide |
| --- | --- | --- | --- |
| Vinnie Russo | de D a B | 0 | un auto sin un rasguño |
| Lola Navarro | de C a S | 60 | un repintado, con un mecánico conectado |
| Dmitri Volkov | de B a S | 200 | tuning, y un auto impecable cuando confía en ti |

<Info>
  Con los fixers desactivados, o cuando ningún fixer compra la clase, la oferta es anónima y no tiene petición.
</Info>
