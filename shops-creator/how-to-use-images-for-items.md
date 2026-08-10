---
title: "How to use images for items"
description: "Configure custom item images shown in the shop UI."
icon: "image"
---

## Global method

The script allows you to use the images you want for the items, bound to their names — so if an item is named `bread`, the image must be named `bread.png`.

You can place the images you want in the `shops_creator/html/images/` folder.

## I want to get the image files from an inventory

To customize the default path where the script looks for images, open the file `shops_creator/integrations/cl_integrations.lua` and edit the `IMAGES_PATH` variable to anything you want.
