---
title: "Jaksam Identity"
description: "Documentation officielle du script FiveM Jaksam Identity : pièces d'identité, licences, mairies, ateliers de faussaires et descentes de police."
icon: "id-card"
---

Ceci est la documentation officielle de **Jaksam Identity**.

Jaksam Identity transforme les pièces d'identité et les licences en vrais items d'inventaire : carte d'identité, permis de conduire avec catégories, permis de port d'arme, cartes de service et cartes de visite, chacun avec une vue de carte en 3D. À côté du côté légal, il ajoute une économie complète de la contrefaçon, avec des ateliers possédés par les jobs, des ouvriers PNJ, une file de commandes et des descentes de police.

<CardGroup cols={2}>
  <Card title="Boutique" icon="cart-shopping" href="https://fivem.jaksam-scripts.com/">
    Achète ou consulte le script sur la boutique jaksam.
  </Card>

  <Card title="Démonstration" icon="play" href="https://youtu.be/3Z_h05D65QI">
    Regarde la démonstration complète sur YouTube.
  </Card>

  <Card title="Langues prises en charge" icon="language">
    Anglais, Allemand
  </Card>
</CardGroup>

## Ce qu'il fait

<CardGroup cols={2}>
  <Card title="Documents en items" icon="id-card">
    Carte d'identité, permis de conduire avec catégories, permis de port d'arme, cartes de service et cartes de visite avec vue de carte en 3D (tourner, retourner, lampe UV).
  </Card>

  <Card title="Mairies" icon="building-columns">
    Un PNJ au guichet pour demander, renouveler, remplacer, déclarer un document perdu ou volé et rendre les anciennes cartes.
  </Card>

  <Card title="Contrôle au registre" icon="magnifying-glass">
    Les autorités voient si un document est authentique, suspendu, expiré, a des catégories retirées ou n'a aucune fiche.
  </Card>

  <Card title="Ateliers de faussaires" icon="print">
    Ateliers possédés par les jobs avec photo, saisie, impression, plastification, gaufrage et découpe. La qualité décide quels défauts se voient.
  </Card>

  <Card title="Ouvriers PNJ et commandes" icon="users-gear">
    Embauche des ouvriers, mets des commandes en file avec priorité, gère tout depuis l'ordinateur portable du patron.
  </Card>

  <Card title="Descentes" icon="building-shield">
    Les agents enfoncent la porte, saisissent les preuves et mettent l'atelier sous scellés.
  </Card>
</CardGroup>

## Documentation

<CardGroup cols={2}>
  <Card title="Installation" icon="download" href="/fr/jaksam-identity/installation">
    Installe Jaksam Identity et fais-le tourner sur ton serveur.
  </Card>

  <Card title="Guides" icon="book-open" href="/fr/jaksam-identity/guides/documents-and-register">
    Documents, mairies, ateliers, descentes, réglages en jeu et commandes.
  </Card>

  <Card title="FAQ" icon="circle-question" href="/fr/jaksam-identity/faq">
    Questions fréquemment posées.
  </Card>

  <Card title="Référence développeur" icon="code" href="/fr/jaksam-identity/server">
    Exports, events et hooks pour les développeurs.
  </Card>
</CardGroup>

## Frameworks pris en charge

<CardGroup cols={3}>
  <Card title="ESX" icon="code" href="/fr/jaksam-identity/installation">
    Licences depuis les tables esx_license, prise en charge optionnelle d'esx_dmvschool.
  </Card>

  <Card title="QBCore" icon="code" href="/fr/jaksam-identity/installation">
    Licences depuis les métadonnées du personnage, qb-inventory 2.2 pris en charge.
  </Card>

  <Card title="Qbox" icon="code" href="/fr/jaksam-identity/installation">
    Remplace qbx_idcard, fonctionne avec les items de départ de qbx_core et qbx_cityhall.
  </Card>
</CardGroup>
