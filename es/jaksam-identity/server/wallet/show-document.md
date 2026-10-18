---
title: "Show document"
description: "Muestra un documento que lleva el jugador a otro jugador cercano como tarjeta 3D."
icon: "eye"
---

Muestra a otro jugador un documento que se lleva encima como tarjeta 3D, igual que si se mostrara desde el inventario. El jugador debe llevar el documento, y los dos jugadores deben estar en la misma instancia y dentro de `Config.ShowDistance`.

<CodeGroup>

```lua Export
exports["jksm_identity"]:ShowDocument(playerId, targetId, serial)
```

```lua Example
RegisterNetEvent("my_phone:showCard", function(targetId, serial)
    local ok, reason = exports["jksm_identity"]:ShowDocument(source, targetId, serial)
    if not ok then
        TriggerClientEvent("my_phone:notify", source, "Could not show the card: " .. reason)
    end
end)
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `playerId` | integer | ID de servidor del jugador que muestra el documento |
| `targetId` | integer | ID de servidor del jugador que lo ve |
| `serial` | string | El número de un documento que lleva el jugador |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `ok` | boolean | **true** si se mostró la tarjeta |
| `reason` | string \| nil | `bad_target` (no válido o el mismo jugador), `too_far` (otra instancia o demasiado lejos), `no_card` (el jugador no lleva ese documento) |
