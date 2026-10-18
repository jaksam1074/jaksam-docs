---
title: "Phone number"
description: "Print the phone number of another phone script on business cards."
icon: "phone"
---

The phone number printed on business cards comes from `Bridge.Phone.Number`. `Config.Bridge.phone` picks RoadPhone (`'roadphone'`) or nothing (`'none'`).

To use another phone script, edit `bridge/phone.lua`:

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

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `src` | integer | Server ID of the player |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `number` | string | The phone number, or `""` if unknown |
