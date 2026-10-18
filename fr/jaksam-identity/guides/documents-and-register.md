---
title: "Documents et registre"
description: "Comment fonctionnent les documents, les catégories de licence, le registre et les fausses cartes dans Jaksam Identity, et comment ajouter tes propres types de documents."
icon: "id-card"
---

## Comment ça marche

<CardGroup cols={2}>
  <Card title="Le document est l'identité" icon="id-card">
    Un contrôle renvoie l'identité imprimée sur le document. Le script ne vérifie jamais qui le porte : un vrai document volé fonctionne jusqu'à ce que son propriétaire le déclare.
  </Card>

  <Card title="Seul le serveur sait ce qui est vrai" icon="server">
    Les vrais numéros sont dans le registre (`jksm_identity_documents`), les faux dans `jksm_identity_forgeries` avec leur qualité. Un vrai et un faux item portent exactement les mêmes métadonnées.
  </Card>

  <Card title="Des faits, pas de la contrainte" icon="scale-balanced">
    L'expiration, les suspensions et les vieilles photos s'affichent sur la carte et au contrôle du registre. Rien n'est retiré, bloqué ou renouvelé automatiquement : la suite, c'est du roleplay.
  </Card>

  <Card title="Le framework garde les licences" icon="list-check">
    ESX : les tables esx_license (`licenses`, `user_licenses`). QBCore/Qbox : les métadonnées du personnage `licences`.
  </Card>
</CardGroup>

<Note>
  **Anonymat :** la photo est prise sur un clone local, non synchronisé, du personnage, sans masque, chapeau ni lunettes. Personne autour ne voit le visage, et la photo ne montre aucun masque.
</Note>

## Types de documents

Les types de documents se configurent dans `Config.Documents` (`config/documents.lua`). Il y a trois sortes :

| Sorte | Valide au registre quand | Exemple |
| --- | --- | --- |
| `identity` | le statut de la fiche est valide | Carte d'identité |
| `license` | le statut est valide **et** la licence (ou au moins une de ses catégories) est toujours détenue | Permis de conduire (catégories A, B, C), permis de port d'arme |
| `badge` | le statut est valide **et** le propriétaire a toujours le job | LSPD, LSMD, LSC |

Chaque entrée a ces champs :

| Champ | Description |
| --- | --- |
| `item` | Le nom de l'item d'inventaire (l'item doit exister dans ton inventaire) |
| `kind` | `identity`, `license` ou `badge` |
| `license` | (`license` uniquement) le type de licence : ESX la table `licenses`, QBCore/Qbox la clé dans les métadonnées `licences` |
| `licenses` | (`license` uniquement, à la place de `license`) un document pour plusieurs types de licence, chacun une catégorie |
| `job` | (`badge` uniquement) le job auquel appartient la carte |
| `validityDays` | Jours avant expiration, `nil` pour jamais |
| `layout` | `id` (paysage, par défaut) ou `badge` (carte de service en portrait) |
| `theme` | Apparence de la carte : en-tête, titre, couleurs. Les cartes de service ont aussi `word`, `emblem` (`star`, `shield`, `starOfLife`, `wrench`), `authority` et `authorityName` |

### Catégories de licence

Un document peut couvrir plusieurs types de licence comme catégories :

```lua
drive = {
    item = 'driver_license',
    kind = 'license',
    licenses = { drive_bike = 'A', drive = 'B', drive_truck = 'C' },
    label = L('doc_driver'),
    validityDays = 180,
},
```

La carte imprime les catégories détenues au moment de la délivrance. Le contrôle du registre montre les catégories détenues maintenant et nomme chaque catégorie imprimée qui a été retirée.

### Ajouter ton propre document

Toute licence de ton framework peut devenir un document. Ajoute l'item à ton inventaire, puis une entrée ici :

```lua
hunting = { item = 'hunting_license', kind = 'license', license = 'hunting', label = 'Hunting licence', validityDays = 120 },
```

### Métadonnées de l'item

Chaque document porte les mêmes champs : `serial`, `firstname`, `lastname`, `dob`, `sex`, `issued`, `expires`, `photo`, et `classes` avec les catégories de licence. `photo` n'est qu'un ID de photo : l'image est dans la table `jksm_identity_photos`.

## Statuts du registre

Chaque vrai document a un statut dans le registre :

| Statut | Signification |
| --- | --- |
| `valid` | Rien à signaler |
| `lost` / `stolen` | Déclaré par le propriétaire dans une mairie |
| `seized` | Saisi par une autorité |
| `suspended` | Suspendu jusqu'à une date fixée, de nouveau valide ensuite |
| `replaced` | Un document plus récent du même type a été délivré au propriétaire |
| `revoked` | Retiré définitivement |

Un nouveau document remplace toujours l'ancien : l'ancien document valide de ce type est marqué `replaced`.

## Le contrôle au registre

Le contrôle au registre, c'est ce que voit une autorité. Il signale :

- **Aucune fiche :** le numéro est inconnu, et si une personne avec le nom imprimé existe
- **Statut :** perdu, volé, saisi, suspendu, remplacé ou retiré
- **Expiré :** la date d'expiration est passée
- **Licence manquante / catégorie retirée :** la licence, ou une des catégories imprimées, n'est plus détenue
- **A quitté le job :** le propriétaire de la carte de service n'a plus ce job
- **Données différentes :** le nom ou la date de naissance imprimés ne correspondent pas au registre

Il ne révèle jamais qui a fait un faux ni sa qualité. Les admins le voient avec `/documents truth <serial>`.

## Utiliser et montrer un document

`Config.UseAction` décide de ce que fait l'utilisation d'un item de document :

| Valeur | Comportement |
| --- | --- |
| `auto` | Le montre au joueur le plus proche dans `Config.ShowDistance`, le regarde s'il n'y a personne |
| `view` | Le regarde toujours |
| `show` | Le montre toujours |
| `menu` | Demande à chaque fois |

Les documents ne sont montrés qu'aux joueurs de la même instance. **Montré de loin, seuls les gros défauts se voient**, en main tu as le regard de près.

## Faux documents et anomalies

Une fausse carte montre des défauts sur trois niveaux. Combien dépend de sa qualité :

| Niveau | Exemples |
| --- | --- |
| Au premier coup d'œil | Sceau décalé, mauvaise police, couleur à côté |
| En main | Photo floue, texte mal aligné, micro-impression manquante, hologramme plat |
| Sous UV | Marque UV manquante |

Le niveau UV apparaît tant que celui qui regarde porte l'item lampe UV (`Config.UvItem`, par défaut `uv_lamp`). Un bon faux peut passer tous les contrôles visuels et n'échouer qu'au registre.

<Info>
  Un document créé par une boutique jaksam ou un don d'admin est **enregistré** (authentique), sauf si sa `rarity` jaksam est listée dans `Config.UnregisteredRarities`. Il devient alors un faux non enregistré avec la qualité `Config.UnregisteredQuality`.
</Info>
