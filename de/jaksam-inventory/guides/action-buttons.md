---
title: "Action Buttons"
icon: "square-plus"
description: "Eigene, immer sichtbare Buttons zur Inventar-Toolbar hinzufügen, für Menüs, Jobs und Schnellaktionen"
---

Action Buttons sind eigene Buttons, die in der Inventar-UI-Toolbar erscheinen. Anders als [Context Actions](/de/jaksam-inventory/guides/context-actions) (die beim Rechtsklick auf ein Item erscheinen) sind Action Buttons immer im Inventar-Header sichtbar und können beliebige eigene Logik auslösen.

<Columns cols={2}>
  <Frame>
    ![Action buttons screenshot](/images/action-buttons-1.jpg)
  </Frame>

  <Frame>
    ![Action buttons 2nd screenshot](/images/action-buttons-2.jpg)
  </Frame>
</Columns>

## Wann Action Buttons nutzen

Nutze Action Buttons, wenn du Folgendes brauchst:

- Einen Button, der immer im Inventar sichtbar ist (nicht itemspezifisch)
- Schnellzugriff auf Funktionen wie "Polizeimenü", "Garage", "Crafting", usw.
- Job- oder rollenspezifische Aktionen

## Grundlegende Nutzung

### Einen Button registrieren

```lua
exports['jaksam_inventory']:registerActionButton(
    'my_button',           -- Eindeutige ID
    'bi-star-fill',        -- Bootstrap Icons Klasse
    'My Tooltip',          -- Tooltip beim Hovern (oder nil)
    function()             -- Klick-Callback
        print('Clicked!')
    end,
    true                   -- Sichtbar (Standard: true)
)
```

### Einen Button entfernen

```lua
exports['jaksam_inventory']:unregisterActionButton('my_button')
```

### Anzeigen/Verstecken ohne zu entfernen

```lua
-- Verstecken (Button bleibt registriert, ist nur unsichtbar)
exports['jaksam_inventory']:hideActionButton('my_button')

-- Wieder anzeigen
exports['jaksam_inventory']:showActionButton('my_button')
```

## Praktische Beispiele

<Tabs>
  <Tab title="Jobspezifisch (Polizei)">
    Registriere den Button einmal beim Start der Resource und zeige/verstecke ihn dann je nach Job:

    ```lua
        -- Beim Resource-Start registrieren (standardmäßig versteckt)
        CreateThread(function()
            exports['jaksam_inventory']:registerActionButton(
                'police_menu',
                'bi-shield-check',
                'Police Actions',
                function()
                    TriggerEvent('police:openActionsMenu')
                end,
                false -- Startet versteckt
            )
        end)
    
        -- Je nach Jobwechsel anzeigen/verstecken
        AddEventHandler('esx:setJob', function(job)
            if job.name == 'police' then
                exports['jaksam_inventory']:showActionButton('police_menu')
            else
                exports['jaksam_inventory']:hideActionButton('police_menu')
            end
        end)
    
        -- Auch beim Spieler-Laden prüfen
        RegisterNetEvent('esx:playerLoaded', function(xPlayer)
            if xPlayer.job.name == 'police' then
                exports['jaksam_inventory']:showActionButton('police_menu')
            end
        end)
    ```
  </Tab>
  <Tab title="Ein Stash öffnen">
    ```lua
        exports['jaksam_inventory']:registerActionButton(
            'open_personal_stash',
            'bi-box-seam',
            'Personal Stash',
            function()
                exports['jaksam_inventory']:openInventory('personal_stash_' .. GetPlayerServerId(PlayerId()))
            end
        )
    ```
  </Tab>
  <Tab title="Crafting-Menü">
    ```lua
        exports['jaksam_inventory']:registerActionButton(
            'crafting_menu',
            'bi-hammer',
            'Crafting',
            function()
                TriggerEvent('crafting:openMenu')
            end
        )
    ```
  </Tab>
  <Tab title="Mehrere Job-Buttons">
    ```lua
        local jobButtons = {
            police = { id = 'btn_police', icon = 'bi-shield-check', tooltip = 'Police Menu', event = 'police:menu' },
            ambulance = { id = 'btn_ambulance', icon = 'bi-heart-pulse', tooltip = 'EMS Menu', event = 'ambulance:menu' },
            mechanic = { id = 'btn_mechanic', icon = 'bi-tools', tooltip = 'Mechanic Tools', event = 'mechanic:menu' },
        }
    
        -- Alle Buttons versteckt registrieren
        CreateThread(function()
            for _, btn in pairs(jobButtons) do
                exports['jaksam_inventory']:registerActionButton(
                    btn.id,
                    btn.icon,
                    btn.tooltip,
                    function()
                        TriggerEvent(btn.event)
                    end,
                    false
                )
            end
        end)
    
        -- Den richtigen Button je nach Job anzeigen
        AddEventHandler('esx:setJob', function(job)
            -- Alle Job-Buttons verstecken
            for _, btn in pairs(jobButtons) do
                exports['jaksam_inventory']:hideActionButton(btn.id)
            end
    
            -- Den für den aktuellen Job anzeigen (falls vorhanden)
            if jobButtons[job.name] then
                exports['jaksam_inventory']:showActionButton(jobButtons[job.name].id)
            end
        end)
    ```
  </Tab>
</Tabs>

## Wichtige Hinweise

<CardGroup cols={1}>
  <Card title="Eindeutige IDs" icon="fingerprint">
    Jeder Button muss eine eindeutige ID haben. Eine erneute Registrierung mit der gleichen ID überschreibt den vorherigen Button.
  </Card>

  <Card title="Persistenz" icon="rotate">
    Buttons überstehen das Öffnen/Schließen des Inventars, gehen aber beim Neustart der Resource verloren. Registriere sie beim Start deiner Resource erneut.
  </Card>

  <Card title="Performance" icon="gauge-high">
    Buttons nicht wiederholt registrieren/entregistrieren. Einmal registrieren, dann mit show/hide die Sichtbarkeit umschalten.
  </Card>
</CardGroup>
