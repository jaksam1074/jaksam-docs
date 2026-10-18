---
title: "Get wallet documents"
description: "Obtén los documentos que lleva un jugador, como datos de tarjeta para una cartera de móvil."
icon: "wallet"
---

Devuelve los documentos que el jugador lleva encima: primero el inventario principal, luego los contenedores de `Config.WalletContainers`. Un documento falso o robado muestra lo que lleva impreso: nunca se consulta el registro.

<CodeGroup>

```lua Export
exports["jksm_identity"]:GetWalletDocuments(playerId)
```

```lua Example
lib.callback.register("my_phone:getWallet", function(source)
    local cards = {}
    for _, document in ipairs(exports["jksm_identity"]:GetWalletDocuments(source)) do
        cards[#cards + 1] = {
            serial = document.serial,
            title = document.title,
            name = document.firstname .. " " .. document.lastname,
            color = document.color,
            photo = document.photo,
        }
    end
    return cards
end)
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `playerId` | integer | ID de servidor del jugador |

### Valor de retorno

Una lista de tablas, una por documento que lleva:

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `serial` | string | El número del documento |
| `type` | string | El tipo de documento, una clave de `Config.Documents` |
| `kind` | string | `identity`, `license` o `badge` |
| `label` | string | La etiqueta del documento |
| `title` | string | El título de la tarjeta según el tema, por ejemplo `DRIVER LICENSE` |
| `color`, `accent` | string | Los colores del tema (hex) |
| `firstname`, `lastname`, `dob`, `sex` | string | La identidad impresa |
| `classes` | string | Las clases de licencia impresas |
| `rank` | string | Solo placas: el rango impreso |
| `issued`, `expires` | string | Las fechas impresas |
| `issuedAt`, `expiresAt` | integer \| nil | Las fechas impresas como tiempos unix |
| `valid` | boolean | Si la fecha de caducidad impresa no ha pasado. Es lo que dice la tarjeta, nunca el registro |
| `photo` | string \| nil | La foto como data URL, **nil** para un documento sin foto |
