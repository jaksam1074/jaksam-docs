---
title: "Mairies"
description: "Documents de départ, mairies avec un PNJ au guichet, frais, et l'intégration d'esx_dmvschool."
icon: "building-columns"
---

## Documents de départ

Chaque personnage qui n'a jamais eu de document des types listés en reçoit un après le chargement, dès que son nom et sa date de naissance sont définis.

```lua
Config.Starter = {
    documents = { 'id_card' },
    delaySeconds = 15,          -- after the character has loaded
}
```

Les documents de départ **n'ont pas de photo** : la photo se prend à la mairie lors d'un renouvellement. Mets `documents = {}` pour désactiver.

## Mairies

Une mairie est un PNJ à un guichet, avec un blip sur la carte. Chaque mairie gère les types de documents qu'elle liste. Les joueurs peuvent :

- **Demander** un premier document
- Le **renouveler** : même numéro, nouvelle expiration et photo (il faut avoir le document sur soi)
- **Obtenir un duplicata** s'il a été perdu ou volé : nouveau numéro, l'ancien devient invalide
- **Déclarer** un document perdu ou volé, ou **déclarer qu'il a été retrouvé**
- **Rendre** leurs propres cartes qui ne sont plus valides
- **Ajouter une catégorie** obtenue après l'impression de la carte (fait un renouvellement)

La photo se prend au guichet. Un document suspendu, retiré ou saisi bloque le guichet pour ce type. **Les cartes de service ne sont jamais délivrées ici**, c'est le patron du job qui s'en charge.

<Note>
  Une carte qui n'appartient pas au joueur reçoit la même réponse, qu'elle soit à quelqu'un d'autre ou fausse : la mairie ne peut donc pas servir à tester des faux.
</Note>

### Configuration

Les mairies se configurent dans `Config.Offices` (`config/office.lua`), ou se placent en jeu sur la page des mairies de `/documents config`.

```lua
Config.Offices = {
    payAccount = 'money',       -- 'money' (cash) | 'bank'
    pedDistance = 40.0,         -- a counter NPC exists only while the player is this close (metres)
    fees = {                    -- per document type; 0 = free
        id_card = { first = 100, renew = 50, replace = 150 },
        drive = { first = 250, renew = 100, replace = 300 },
        weapon = { first = 1000, renew = 400, replace = 1200 },
    },
    locations = {
        { label = L('office_city_hall'), coords = vec4(-517.63, -251.57, 35.67, 207.0), model = 'a_f_y_business_01',
          documents = { 'id_card', 'drive' }, blip = { sprite = 498, color = 0, scale = 0.7 } },
    },
}
```

Les frais ne sont payés qu'une fois la photo et la délivrance réussies.

<Tip>
  Tu peux ouvrir une mairie par autorité, par exemple un guichet auto-école qui ne gère que `drive` et un guichet de police qui ne gère que `weapon`.
</Tip>

## esx_dmvschool (ESX uniquement)

esx_dmvschool donne la licence après un examen réussi mais ne remet aucune carte. Avec `Config.DmvSchool` actif :

- le **premier permis de conduire est délivré juste après l'examen**, avec une photo prise sur place et sans frais (l'auto-école a déjà encaissé)
- une catégorie obtenue plus tard est **imprimée sur le permis que le joueur porte** (même numéro, expiration et photo)
- sans la carte sur lui, le joueur est invité à passer à la mairie, qui l'ajoute

```lua
Config.DmvSchool = {
    enabled = true,
    document = 'drive',         -- the document type its licences are classes of
}
```

<Warning>
  L'event `esx_dmvschool:addLicense` n'est pas vérifié côté serveur par esx_dmvschool, un client tricheur peut donc s'attribuer n'importe quelle licence avec. Sécurise l'event dans esx_dmvschool, ou mets `Config.DmvSchool.enabled = false`, sur un serveur en production.
</Warning>

## Mairie QBCore et Qbox

Sur la version QBCore, ce que donnent qb-core, qbx_core et qb-cityhall / qbx_cityhall devient un document enregistré du personnage. qbx_cityhall le délivre avec une photo prise sur place. Sur Qbox, retire `qbx_idcard` : Jaksam Identity répond à sa place.
