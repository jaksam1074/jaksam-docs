---
title: "Telefonnummer"
description: "Die Telefonnummer eines anderen Handy-Scripts auf Visitenkarten drucken."
icon: "phone"
---

Die auf Visitenkarten gedruckte Telefonnummer kommt von `Bridge.Phone.Number`. `Config.Bridge.phone` wählt RoadPhone (`'roadphone'`) oder nichts (`'none'`).

Um ein anderes Handy-Script zu nutzen, bearbeite `bridge/phone.lua`:

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

### Parameter

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `src` | integer | Server-ID des Spielers |

### Rückgabewert

| Name | Datentyp | Beschreibung |
| --- | --- | --- |
| `number` | string | Die Telefonnummer, oder `""`, wenn unbekannt |
