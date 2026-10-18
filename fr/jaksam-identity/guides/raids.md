---
title: "Descentes"
description: "Laisse les jobs de police enfoncer les ateliers de faussaires, saisir les preuves et les mettre sous scellés."
icon: "building-shield"
---

Les agents enfoncent la porte d'un atelier, le fouillent et le mettent sous scellés. Les descentes se configurent dans `Config.Raid` (`config/raid.lua`) ou sur la page des descentes de `/documents config`. `Config.Raid.enabled = false` les désactive.

## Unités

Un ou plusieurs jobs qui font les descentes ensemble, à partir d'un grade que tu choisis, avec une salle des scellés à un endroit que tu choisis :

```lua
forces = {
    police = { label = 'LSPD', jobs = { 'police' }, minGrade = 0, locker = vec4(452.3, -980.0, 30.69, 90.0) },
},
```

<Warning>
  Place la salle des scellés de chaque unité en jeu (page des descentes de `/documents config`). **Sans salle des scellés, rien ne peut être saisi.**
</Warning>

## Déroulement d'une descente

<Steps>
  <Step title="Enfoncer la porte">
    À la porte d'un atelier qui a un propriétaire. Il faut assez d'agents en service connectés (`minOfficers`), l'item `door_ram` (`item`, `''` pour aucun) et du temps : le temps d'effraction du niveau de sécurité de l'atelier (30 secondes, 90 avec l'amélioration). L'agent reste à la porte : s'éloigner ou annuler l'arrête.
  </Step>
  <Step title="L'alerte">
    Avec un garde de sécurité embauché, tout le monde à l'intérieur est prévenu et voit le compte à rebours. Sans garde, personne à l'intérieur ne remarque rien. Avec l'amélioration de sécurité, les membres ailleurs reçoivent une alarme.
  </Step>
  <Step title="Détruire les preuves">
    Les membres prévenus détruisent les preuves aux quatre broyeuses pendant le compte à rebours : toutes les commandes en cours, ou ce qu'il y a dans un stockage. Les ouvriers aussi : sur la page Personnel du portable, le patron choisit ce qu'ils détruisent quand le garde donne l'alarme, et ils se partagent les tâches. Ce qui n'est pas fait quand la porte cède reste.
  </Step>
  <Step title="La porte ouverte">
    La porte reste ouverte `openMinutes`. Les agents entrent, les ouvriers et le garde lèvent les mains, et aucun poste, ordinateur ou portable de l'atelier n'accepte d'action. À chaque étagère, un agent vide le stockage dans la salle des scellés de l'unité. Sur le portable du patron, l'équipement est saisi (`equipmentLoss`).
  </Step>
  <Step title="Mise sous scellés">
    Un agent met l'atelier sous scellés à sa porte, ou le temps s'écoule. Tout le monde à l'intérieur est mis dehors, et pendant `sealHours` personne du job propriétaire ne peut entrer. Les ouvriers ne font rien pendant ce temps et ne sont pas payés pour cette période.
  </Step>
</Steps>

Un atelier peut être de nouveau enfoncé `cooldownHours` après la dernière effraction. Les scellés se lèvent tout seuls. Un atelier qui perd son propriétaire perd ses scellés, et un redémarrage en pleine descente laisse l'atelier sous scellés.

## Configuration

```lua
Config.Raid = {
    enabled = true,
    minOfficers = 2,            -- officers of all forces that must be online (0 = no minimum)
    dutyOnly = true,            -- only officers on duty count and act
    item = 'door_ram',          -- the item a breach needs ('' = none)
    consumeItem = true,         -- the item is used up when the door gives way
    warnNeedsGuard = true,      -- those inside are warned only when the workshop has a security guard
    alarmNeedsSecurity = true,  -- members elsewhere are alarmed only with the security upgrade
    openMinutes = 20,           -- the door stays open this long unless sealed earlier
    sealHours = 12,             -- nobody of the owning job gets in for this long (0 = no seal)
    cooldownHours = 24,         -- no new breach for this long after a breach
    retryMinutes = 5,           -- a breach given up can be tried again after this long
    equipmentLoss = 'level',    -- 'level' one level down | 'all' gone | 'nothing' cannot be seized
    seizeSeconds = 10,
    shredWhile = 'breach',      -- 'breach' only during the countdown | 'raid' until the raid is over
    shredSeconds = 8,
    workersShred = true,
    locker = { slots = 200, weight = 2000.0 },
}
```

## Commandes admin

| Commande | Ce qu'elle fait |
| --- | --- |
| `/documents raid` | Liste les descentes et les scellés |
| `/documents raid <workshop> end` | Termine une descente en cours |
| `/documents raid <workshop> unseal` | Lève des scellés |
| `/documents raid <workshop> reset` | Efface aussi l'attente avant la prochaine descente |

## Dispatch et barre de progression

- `Editable.CanRaid` et `Editable.OnRaid` dans `editable/server.lua` : ajoute tes propres conditions, ou envoie un appel au dispatch. Voir [Peut faire une descente](/fr/jaksam-identity/server/hooks/can-raid) et [Pendant une descente](/fr/jaksam-identity/server/hooks/on-raid).
- `Editable.Progress` dans `editable/client.lua` : remplace la barre de progression. Voir [Barre de progression](/fr/jaksam-identity/client/progress-bar).

L'item `door_ram` est dans les trois fichiers d'items du dossier install, son image dans `install/images/`.
