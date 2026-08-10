---
title: "Get item image path"
description: "Gets the NUI image path for an item, with fallback to a default image if none is found."
icon: "image"
---

Gets the NUI image path for an item. The function uses a fallback system: first checks if the item has a custom `image` field, then tries to find `.png` or `.webp` files, and finally falls back to the default `box.webp` image.

<CodeGroup>

```lua Export
exports['jaksam_inventory']:getItemImagePath(itemName)
```

```lua Example
local imagePath = exports['jaksam_inventory']:getItemImagePath('bread')
print(imagePath) -- nui://jaksam_inventory/_images/bread.png

-- Item with custom image field
local customImage = exports['jaksam_inventory']:getItemImagePath('custom_item')
print(customImage) -- nui://jaksam_inventory/_images/custom_image.png (if item.image is set)

-- Item not found returns default box image
local notFound = exports['jaksam_inventory']:getItemImagePath('invalid_item')
print(notFound) -- nui://jaksam_inventory/_images/box.webp
```

</CodeGroup>

### Parameters

| Name | Data Type | Description |
| --- | --- | --- |
| `itemName` | string | The name of the item to get the image path for |

### Return value

| Name | Data Type | Description |
| --- | --- | --- |
| `imagePath` | string | The NUI image path (e.g., "nui://jaksam_inventory/_images/bread.png"). Always returns a valid path, using fallback to `box.webp` if the item doesn't exist or no image is found |
