---
title: "Ajustes en el juego"
description: "Cambia tasas, oficinas, talleres, precios, sueldos y reglas de redada en el juego con /documents config, sin reiniciar."
icon: "sliders"
---

Los admins cambian la mayoría de los ajustes en el juego con `/documents config`: sin archivos que editar, sin reiniciar.

## Qué incluye

| Sección | Ajustes |
| --- | --- |
| **General** | Usar y mostrar documentos, números de documento, idioma |
| **Oficinas** | Documentos iniciales, tasas, las propias oficinas |
| **Talleres** | Los talleres con precio y dueño, reglas de compra y venta, precios de mejoras, pedidos de material, almacenes, reglas de falsificación y pedidos |
| **Trabajadores** | Precios de contratación, sueldos, tiempos de trabajo, modo demo |
| **Redadas** | Reglas, cuerpos con sus armarios de pruebas, la puerta, la incautación |

## Cómo funciona

- **Los cambios se acumulan y se aplican juntos.** Lo que cambias queda marcado, y una barra abajo lo guarda todo (**Apply**) o lo descarta (**Discard**). Nada llega a los jugadores antes.
- **Los lugares se fijan con la cámara.** **Place** te deja moverte y apuntar: un fantasma del NPC aparece donde miras, la rueda del ratón lo gira, un clic fija el lugar. **Here** coge el punto donde estás, y te puedes teletransportar a un lugar guardado.
- **Los trabajos se eligen de la lista del framework.** Los tiempos se muestran en segundos, minutos, horas o días, las probabilidades en porcentaje.
- **Efectivo al momento** para todos en el servidor tras **Apply**. Una excepción marcada espera al siguiente arranque del script: el tamaño de los almacenes.
- **El idioma** cambia al momento para todos: menús, targets, blips y las etiquetas de la config.

## Archivos y base de datos

Los archivos de config siguen siendo los valores por defecto. Un valor cambiado se guarda en la base de datos (tabla `jksm_identity_settings`) y tiene prioridad sobre el archivo. Cada valor puede volver a su valor por defecto con un clic, y cada cambio se escribe en el log con el admin que lo hizo.

<Note>
  Estos siguen en `config/main.lua`, porque hacen falta mientras el script carga: framework, inventario y target, los permisos de admin, `Config.Debug` y los nombres de los items.
</Note>
