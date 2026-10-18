---
title: "Comandos"
description: "Lista completa de los comandos de admin /documents y de los comandos de jugador de Jaksam Identity."
icon: "slash-forward"
---

## Quién puede usarlos

`/documents <subcomando>` funciona desde la consola del servidor, para jugadores con el ACE `jksm_identity.admin` y para los grupos del framework de `Config.AdminGroups`. Sin subcomando los lista todos.

```cfg
add_ace group.admin jksm_identity.admin allow
```

El nombre del comando es `Config.AdminCommand` (por defecto `documents`).

## Comandos de admin

| Subcomando | Qué hace |
| --- | --- |
| `config` | Abre los [ajustes en el juego](/es/jaksam-identity/guides/settings-in-game) |
| `issue <playerId> <type> [nophoto] [force] [grant] [grant:<licence type>]` | Expide un documento real |
| `check <serial>` | Consulta del registro como la ve una autoridad |
| `truth <serial>` | Vista de admin: real, falso (con calidad y autor) o desconocido |
| `license <playerId> list \| add <type> \| remove <type>` | Licencias de un personaje |
| `forge <playerId> <type> <quality 0-100> [nophoto] [copy:<serial>]` | Da una falsificación |
| `workshop <job> \| leave` | Entra o sale de un taller |
| `exit <playerId> \| all` | Saca jugadores de los talleres |
| `toner <job> <prints>` | Fija el tóner de la impresora de un taller |
| `raid [<workshop> [end \| unseal \| reset]]` | Lista redadas y precintos, termina una redada, quita un precinto, borra la espera hasta la siguiente redada |
| `order <job> <type> <amount> [low\|normal\|urgent] [assignee]` | Crea un pedido |
| `orders <job>` | Lista los pedidos de un taller |
| `ordercmd <job> <id> <action> [value]` | Gestiona un pedido |
| `demo on \| off \| refill` | Modo demo para presentaciones (`Config.Demo`) |

### Opciones de issue

| Opción | Efecto |
| --- | --- |
| `nophoto` | Expide sin hacer foto |
| `force` | Expide aunque falte la licencia o el trabajo |
| `grant` | Da además al personaje todas las licencias del documento |
| `grant:<licence type>` | Da además al personaje una licencia, por ejemplo `grant:drive_truck` |

```bash
/documents issue 12 id_card            # ID card with photo for player 12
/documents issue 12 drive grant        # driver licence, granting the licence first
/documents check SAAB1234567           # what the police would see
/documents forge 12 drive 80           # a forged driver licence of quality 80
```

<Note>
  Con `Config.Debug = true` también hay comandos de medición (`/jksm_pos`, `/jksm_aim`, ...) y subcomandos de prueba, solo para admins. Desactiva `Config.Debug` en un servidor en producción: así no existen.
</Note>

## Comandos de jugador

| Comando | Qué hace |
| --- | --- |
| `/businesscards` | Imprime tarjetas de visita de tu trabajo, mira [Tarjetas de visita](/es/jaksam-identity/guides/business-cards) |
