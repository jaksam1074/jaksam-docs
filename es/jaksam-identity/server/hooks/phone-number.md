---
title: "Phone number"
description: "Imprime el número de teléfono de otro script de móvil en las tarjetas de visita."
icon: "phone"
---

El número de teléfono impreso en las tarjetas de visita sale de `Bridge.Phone.Number`. `Config.Bridge.phone` elige RoadPhone (`'roadphone'`) o nada (`'none'`).

Para usar otro script de móvil, edita `bridge/phone.lua`:

<CodeGroup>

```lua Function
function Bridge.Phone.Number(src)

end
```

```lua Example
function Bridge.Phone.Number(src)
    local ok, number = pcall(function() return exports["my_phone"]:GetNumber(src) end)
    return ok and number and tostring(number) or ""
end
```

</CodeGroup>

### Parámetros

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `src` | integer | ID de servidor del jugador |

### Valor de retorno

| Nombre | Tipo de dato | Descripción |
| --- | --- | --- |
| `number` | string | El número de teléfono, o `""` si no se conoce |
