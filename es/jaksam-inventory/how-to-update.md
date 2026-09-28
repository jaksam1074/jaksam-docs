---
title: "Cómo"
icon: "rectangle-new"
tag: "Update"
description: "Mantén tu instalación de Jaksam Inventory actualizada sin perder tus ítems personalizados, ajustes, integraciones u otras personalizaciones."
---

# Actualizar Jaksam Inventory

Desde la versión **1.28**, actualizar es mucho más sencillo: todo lo que cambias vive en su propia carpeta, así que una actualización consiste solo en reemplazar una carpeta. Elige la guía que corresponde a la versión que tienes instalada ahora:

<CardGroup cols={3}>
  <Card title="1.28 y posteriores" icon="bolt">
    Reemplaza una carpeta, sin nada que respaldar ni restaurar.
  </Card>

  <Card title="De 1.27 o anterior a 1.28" icon="right-left">
    Solo una vez: tus personalizaciones se trasladan automáticamente.
  </Card>

  <Card title="Versiones anteriores a 1.28" icon="clock-rotate-left">
    La guía antigua, para instalaciones que siguen en 1.27 o anterior.
  </Card>
</CardGroup>

<Tip>
  Puedes ver la versión instalada en `jaksam_inventory/fxmanifest.lua`, en la línea `version`.
</Tip>

## Versión 1.28 y posteriores

Todo lo que cambias (ajustes, ítems, imágenes, hooks, módulos, traducciones, integraciones) se guarda en **`jaksam_inventory_data`**, una carpeta junto a `jaksam_inventory`. Las actualizaciones solo reemplazan `jaksam_inventory`, así que tus cambios nunca se tocan.

<Steps>
  <Step title="Detén tu servidor">
    Detén tu servidor FiveM antes de reemplazar los archivos.
  </Step>
  <Step title="Reemplaza jaksam_inventory">
    Elimina la carpeta `jaksam_inventory` y pon la nueva en su lugar. Deja `jaksam_inventory_data` exactamente donde está.
  </Step>
  <Step title="Inicia tu servidor">
    Eso es todo: tus ítems, ajustes y personalizaciones siguen ahí.
  </Step>
</Steps>

<Tip>
  Hacer una copia de seguridad de `jaksam_inventory_data` de vez en cuando sigue siendo buena idea: es la única carpeta que contiene todo tu trabajo.
</Tip>

<Warning>
  **No edites archivos dentro de `jaksam_inventory`**, cada actualización los reemplaza. Si lo haces, la consola del servidor te indica al iniciar qué archivo se editó y dónde debe ir ese cambio dentro de `jaksam_inventory_data`. Las versiones incluidas de cada archivo están en `jaksam_inventory/defaults`: léelas, copia lo que necesites, pero no las edites.
</Warning>

### Qué contiene jaksam_inventory_data

| Archivo / Carpeta | Qué contiene |
| --- | --- |
| `current_config.json` | Los ajustes del menú `/inventory` |
| `items.lua` | Tus ítems nuevos, y solo los campos que cambiaste de los ítems por defecto. El menú de administración también escribe aquí |
| `_images/` | Las imágenes de tus ítems, con el nombre del ítem (`bread.png`, `bread.webp`) |
| `variables.css` | Los colores por defecto del inventario. Se definen desde el menú de temas, o pegando la salida del comando F8 `admintheme` |
| `locales/` | Solo los textos que cambiaste |
| `integrations/` | Solo las funciones de integración que cambiaste |
| `_hooks/` | Tus hooks. Un archivo con el mismo nombre que un hook por defecto lo reemplaza |
| `_modules/` | Tus módulos. La misma ruta que un módulo por defecto lo reemplaza |
| `_data/` | Archivos que se ejecutan después de los `_data` por defecto, como el tamaño de los maleteros |
| `components.json` | Componentes de armas cambiados desde el menú de administración |
| `_backups/` | Una copia de `items.lua` antes de cada cambio hecho desde el menú de administración |

<Note>
  `jaksam_inventory_data` no necesita ninguna línea en `server.cfg`: `jaksam_inventory` lo inicia por sí mismo.
</Note>

### Solución de problemas

<AccordionGroup>
  <Accordion title="La consola dice que falta jaksam_inventory_data">
    `jaksam_inventory_data` debe estar junto a `jaksam_inventory`, en la misma carpeta. Vuelve a ponerla (o restáurala desde tu copia de seguridad) y reinicia el servidor. Si nunca tuviste una, se ha creado una vacía para ti: solo reinicia.
  </Accordion>

  <Accordion title="La consola me pide actualizar jaksam_core">
    Tu `jaksam_core` es demasiado antiguo para leer los ajustes desde `jaksam_inventory_data`. Descarga el último `jaksam_core` y reemplázalo. Mientras tanto, tus ajustes siguen funcionando desde su ubicación anterior.
  </Accordion>

  <Accordion title="La consola dice que se editó un archivo de jaksam_inventory">
    Ese cambio se perderá con la próxima actualización. Muévelo al lugar que indica la consola, dentro de `jaksam_inventory_data`.
  </Accordion>
</AccordionGroup>

## Pasar de 1.27 o anterior a 1.28

Solo lo haces una vez. Después, cada actualización es la sencilla de arriba.

<Steps>
  <Step title="Detén tu servidor y haz una copia de seguridad">
    Detén tu servidor y haz una copia de toda tu carpeta `jaksam_inventory`.
  </Step>
  <Step title="Actualiza también jaksam_core">
    Descarga el último `jaksam_core` y reemplaza el tuyo. Las versiones anteriores no pueden leer los ajustes desde su nueva ubicación.
  </Step>
  <Step title="Copia la nueva versión encima de la antigua">
    Copia el nuevo `jaksam_inventory` **encima** del actual, sobrescribiendo los archivos, y pon `jaksam_inventory_data` de la descarga junto a él.

    No elimines antes la carpeta antigua: tus archivos antiguos deben seguir dentro de `jaksam_inventory` en el primer inicio para poder trasladarlos. Si ya la eliminaste, copia `current_config.json`, `_data/`, `_hooks/`, `_modules/`, `integrations/`, `locales/` y tus imágenes personalizadas de `_images/` desde tu copia de seguridad al nuevo `jaksam_inventory` antes de iniciar.
  </Step>
  <Step title="Inicia tu servidor">
    En el primer inicio tus ajustes, ítems, hooks, módulos, integraciones, traducciones e imágenes personalizadas se importan automáticamente en `jaksam_inventory_data`. La consola del servidor y el menú `/inventory` muestran lo que se importó, y los archivos antiguos se mueven a `jaksam_inventory/_migrated`.
  </Step>
</Steps>

<Note>
  Hay dos cosas que no se trasladan automáticamente:

  - **Colores personalizados** de `dist/assets/variables.css`: abre el menú de temas y define tu tema como el predeterminado del servidor, o copia las variables que cambiaste en `jaksam_inventory_data/variables.css`
  - **Traducciones personalizadas del menú** en `dist/menu_translations/`: siguen dentro de `jaksam_inventory`, así que vuelve a copiarlas después de cada actualización
</Note>

## Versiones anteriores a 1.28

<Info>
  Esta es la guía para instalaciones que siguen en la versión 1.27 o anterior, donde tus personalizaciones están dentro de la propia carpeta `jaksam_inventory`.
</Info>

<Warning>
  **Crea siempre una copia de seguridad antes de actualizar.** Nunca elimines tu instalación existente antes de tener una copia de seguridad funcional.
</Warning>

### Antes de Empezar

<Tip>
  **Recomendado:** Conserva tu copia de seguridad durante al menos unos días después de la actualización. Esto facilita revertir los cambios si algo sale mal.
</Tip>

<CardGroup cols={2}>
  <Card title="Detén tu Servidor" icon="server">
    Detén siempre tu servidor de FiveM antes de reemplazar los archivos del inventario.
  </Card>

  <Card title="Crea una Copia de Seguridad" icon="floppy-disk">
    Haz una copia de seguridad de tus archivos y carpetas personalizados antes de instalar la nueva versión.
  </Card>

  <Card title="Instala la Actualización" icon="download">
    Elimina la versión anterior y sube la última versión de Jaksam Inventory.
  </Card>

  <Card title="Restaura las Personalizaciones" icon="rotate">
    Restaura tus archivos respaldados en la nueva instalación.
  </Card>
</CardGroup>

### ¿Qué Debo Respaldar?

#### Siempre Respaldar

Estos archivos y carpetas **siempre** deben incluirse en tu copia de seguridad:

| Archivo / Carpeta | Descripción |
| --- | --- |
| `_data/` | Ítems y ajustes del inventario |
| `_backups/` | Copias de seguridad de la lista de ítems |
| `_hooks/` | Recetas de crafting y lógica personalizada |
| `_modules/` | Integraciones con scripts externos |
| `integrations/` | Ajustes de integración |
| `current_config.json` | Archivo de configuración principal |

#### Archivos Personalizados

Respalda estos únicamente si los has modificado o agregado:

| Archivo / Carpeta | Descripción |
| --- | --- |
| `_images/` | Imágenes personalizadas de ítems |
| `dist/assets/variables.css` | Colores personalizados del tema |
| `_locales/` | Traducciones personalizadas |
| `dist/menu_translations/` | Traducciones personalizadas del menú |

<Note>
  Si no has personalizado ninguno de los archivos mencionados arriba, no necesitas respaldarlos.
</Note>

### Proceso de Actualización

Sigue estos pasos **en orden**.

### Referencia Rápida

| Archivo / Carpeta | Copia de Seguridad Requerida | Propósito |
| --- | :-: | --- |
| `_data/` | Sí | Ítems y ajustes |
| `_backups/` | Sí | Copias de seguridad de la lista de ítems |
| `_hooks/` | Sí | Crafting y lógica personalizada |
| `_modules/` | Sí | Integraciones externas |
| `integrations/` | Sí | Ajustes de integración |
| `current_config.json` | Sí | Configuración principal |
| `_images/` | Personalizado | Imágenes personalizadas de ítems |
| `dist/assets/variables.css` | Personalizado | Personalización del tema |
| `_locales/` | Personalizado | Traducciones personalizadas |
| `dist/menu_translations/` | Personalizado | Traducciones del menú |

### Solución de Problemas

<AccordionGroup>
  <Accordion title="Mis ítems desaparecieron">
    Restaura la carpeta `_data/` desde tu copia de seguridad y reinicia el servidor.
  </Accordion>

  <Accordion title="Faltan mis recetas de crafting">
    Restaura la carpeta `_hooks/` desde tu copia de seguridad.
  </Accordion>

  <Accordion title="Mis ajustes se reiniciaron">
    Restaura `current_config.json` desde tu copia de seguridad.
  </Accordion>

  <Accordion title="Los colores de mi tema se reiniciaron">
    Restaura `dist/assets/variables.css` desde tu copia de seguridad si personalizaste el tema predeterminado.
  </Accordion>

  <Accordion title="Faltan mis imágenes personalizadas">
    Restaura tu carpeta `_images/` personalizada.
  </Accordion>

  <Accordion title="Faltan mis traducciones">
    Restaura `_locales/` y/o `dist/menu_translations/`, según qué archivos de traducción hayas personalizado.
  </Accordion>

  <Accordion title="Mi servidor no inicia">
    1. Asegúrate de que la nueva carpeta `jaksam_inventory` esté instalada correctamente.
    2. Asegúrate de que tus archivos de copia de seguridad se hayan restaurado en las ubicaciones correctas.
    3. Espera aproximadamente 30 segundos después de iniciar el servidor, ya que la base de datos puede estar actualizándose automáticamente.
    4. Revisa la consola de tu servidor en busca de errores.
    5. Si el problema persiste, restaura tu copia de seguridad anterior y contacta con soporte.
  </Accordion>
</AccordionGroup>

### Importante

<Warning>
  **Nunca elimines tu copia de seguridad inmediatamente después de una actualización exitosa.** Consérvala durante unos días por si descubres algún problema más adelante.
</Warning>

<Check>
  Una vez que todo funcione correctamente, tu actualización de Jaksam Inventory estará completa.
</Check>
