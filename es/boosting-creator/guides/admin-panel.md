---
title: "Panel de admin"
description: "El panel de admin de Boosting Creator: contratos en vivo, jugadores en espera, perfiles de jugador, ajustes y logs de Discord."
icon: "sliders"
---

Abre el panel con `/boostingcreator` o `/boostcreator` (mira [Permiso de admin](/es/boosting-creator/installation#permiso-de-admin)). Cada cambio se aplica al momento, sin reiniciar.

| Pestaña | Para qué sirve |
| --- | --- |
| **Clases** | Las [clases](/es/boosting-creator/guides/classes-and-vehicles) y sus riesgos |
| **Vehículos** | Los autos de cada clase |
| **Ubicaciones** | [Todos los lugares](/es/boosting-creator/guides/locations) del script |
| **Fixers** | Los [fixers](/es/boosting-creator/guides/fixers) y sus peticiones |
| **En vivo** | Contratos en curso ahora mismo y jugadores en espera |
| **Jugadores** | Perfiles, reputación, historial y garajes |
| **Ajustes** | Todo lo demás |

## En vivo

Se actualiza cada 5 segundos. Para cada contrato en curso: el jugador (y los miembros de la crew), el fixer y la petición, clase, vehículo y matrícula, ruta, estado con las insignias de rastreador, persecución y portavehículos, y el tiempo restante. **Cancelar** termina un contrato sin cambiar la reputación.

**Jugadores esperando su próximo contrato** muestra quién está en cooldown o en el límite diario, con el tiempo restante y un botón **Quitar cooldown**.

<Frame>
  ![Pestaña Live con un contrato en curso](/images/boosting-creator/panel-live.jpg)
</Frame>

## Jugadores

Todos los perfiles de boosting, primero los jugadores conectados, con búsqueda por nombre o identificador. Haz clic en uno para abrirlo:

- reputación, nivel, contratos completados y fallidos, dinero ganado
- **Fijar reputación** o **Añadir o quitar reputación**
- el garaje con sus autos, y un botón para quitar un auto
- los últimos 25 contratos con fixer, petición y el motivo del final
- un menú de peligro: **Reiniciar perfil**, **Borrar historial**, **Quitarle el garaje**

## Ajustes

| Categoría | Qué contiene |
| --- | --- |
| **General** | Idioma, permiso ACE, item del portátil, cuenta a la que va el pago |
| **Contratos** | Tiempos de las ofertas, cooldowns y límite diario, reputación y pago, VIN scratch, desguace, crews, fixers y confianza, garajes, venta al por mayor e incautación, guardias, persecución de banda, avisos al forzar |
| **Robo** | Minijuego del puente, espera entre intentos y alarma |
| **Rastreador** | Avisos, hackeos y minijuego de hackeo |
| **Módulos** | Mira [Módulos](/es/boosting-creator/modules) |
| **Discord** | Logs y webhooks |

**Restaurar predeterminados** devuelve cada ajuste a como venía con el script. Las clases, las ubicaciones y los fixers no se tocan.

## Logs de Discord

Con los logs de Discord activados, el script registra los finales de contrato (con fixer y petición), los autos que llegaron demasiado rápido para ser reales, los rastreadores desactivados, los VIN borrados, los garajes comprados, los portavehículos incautados, los resultados de minijuego rechazados y cada cambio de admin. Todo va al webhook principal.

Para enviar un tipo de log a otro sitio, añádelo a `specificWebhooks` en `current_config.json`, con los tipos `contracts`, `vin`, `garages`, `admin` y `cheat`.
