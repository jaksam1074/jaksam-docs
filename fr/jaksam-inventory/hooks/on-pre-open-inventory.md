---
title: "Pre open inventory"
description: "Hook déclenché avant qu'un inventaire secondaire soit envoyé au client, peut empêcher son ouverture."
icon: "door-open"
---

Se déclenche AVANT qu'un inventaire secondaire (stash, coffre, boîte à gants, shop, drop, conteneur, l'inventaire d'un autre joueur, ...) soit envoyé au client. Ce hook peut empêcher l'inventaire de s'ouvrir. Enregistre-le avec [`registerHook`](/fr/jaksam-inventory/hooks#enregistrer-un-hook) en utilisant le nom d'event `onPreOpenInventory`.

Ouvrir ton **propre** inventaire de joueur ne déclenche jamais ce hook.

### Payload

| Champ | Type de donnée | Description |
| --- | --- | --- |
| `playerId` | number | Le joueur qui ouvre l'inventaire |
| `inventoryId` | string | par exemple `"stash_07ABC"` |
| `inventoryType` | string | `player`, `stash`, `shop`, `trunk`, `glovebox`, `container`, `ground_container`, `dumpster`, `omnipack` |
| `slotId` | number \| nil | Uniquement pour les conteneurs : le slot de l'item conteneur dans l'inventaire parent |

<Note>
  Ce hook peut empêcher l'inventaire de s'ouvrir en retournant `false`. Les données ne quittent jamais le serveur, c'est donc un vrai point de contrôle d'accès (restriction par job/gang/whitelist), pas seulement une vérification côté UI.
</Note>

**Filtres disponibles :** `inventoryTypeFilter` et `inventoryFilter`.

### Privilégie les hooks sans état

Quand un joueur appuie sur la touche d'inventaire, le client précharge les inventaires à portée (les stashes à moins de 3m d'une position configurée, plus les coffres, boîtes à gants, shops, poubelles et drops à proximité) avant l'ouverture de l'UI, et chaque préchargement déclenche ce hook. Ton callback peut donc s'exécuter plusieurs fois pour le même inventaire, et pour des inventaires que le joueur n'ouvre jamais réellement.

Cela ne concerne que les inventaires ayant des coordonnées configurées - ceux purement virtuels, ouverts programmatiquement par ton propre script, ne sont jamais préchargés. Écris quand même le callback comme une vérification pure sur le job/gang/identifiant lorsque c'est possible. Un motif de token à usage unique (`authorized[source] = inventoryId`, consommé à la première correspondance) est sujet aux races pour un inventaire placé physiquement : un préchargement peut consommer le token avant que la véritable ouverture n'atteigne le hook, et l'ouverture est alors refusée.

<Warning>
  Le message retourné par ce hook n'est pas affiché au joueur, car le préchargement le ferait se répéter. Appelle `notifyPlayer` depuis l'intérieur du hook si tu veux expliquer la raison au joueur.
</Warning>

### À savoir

<AccordionGroup>
  <Accordion title="Stashes privés">
    jaksam ajoute `_<ownerCharIdentifier>` aux IDs des stashes privés, `payload.inventoryId` est donc l'ID entièrement résolu. Les motifs basés sur un préfixe continuent de correspondre, puisque le suffixe est à la fin.
  </Accordion>

  <Accordion title="Conteneurs">
    Bloquer un conteneur empêche seulement son ouverture. Déposer un item sur un sac à dos fermé fonctionne toujours, car il s'agit d'un transfert d'item - utilise [`onItemTransferred`](/fr/jaksam-inventory/hooks/on-item-transferred) pour restreindre ce qui y entre.
  </Accordion>

  <Accordion title="forceOpenInventory déclenche quand même ce hook">
    `forceOpenInventory` contourne les vérifications de permissions propres à jaksam, mais pas tes hooks - comme ox_inventory, dont le hook `openInventory` se déclenche même quand `forceOpenInventory` passe `ignoreSecurityChecks`. Cela signifie qu'un hook peut aussi bloquer un `/openinventory` d'admin, `OpenInventoryById` ou `forceOpenInventoryOX` : filtre donc sur les inventaires qui t'intéressent vraiment plutôt que de refuser par défaut.
  </Accordion>
</AccordionGroup>

### Exemples

<AccordionGroup>
  <Accordion title="Restreindre les stashes de job à leur propre job">
    ```lua
    -- Vérification sans état : sûre même répétée pendant le préchargement
    exports['jaksam_inventory']:registerHook("onPreOpenInventory", function(payload)
        local job = payload.inventoryId:match("^job_stash_(.+)$")
        if job and GetPlayerJob(payload.playerId) ~= job then
            return false
        end
    end, {
        inventoryTypeFilter = {stash = true}
    })
    ```
  </Accordion>
</AccordionGroup>

Voir [l'aperçu des Hooks](/fr/jaksam-inventory/hooks) pour l'API `registerHook`, les filtres disponibles et le comportement des valeurs de retour.
