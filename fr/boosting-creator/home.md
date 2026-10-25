---
title: "Boosting Creator"
description: "Documentation officielle du script FiveM Boosting Creator : contrats de vol de voitures par classe, traceurs GPS, gardes, poursuites par un gang, fixers, garages et porte-voitures."
icon: "car-burst"
---

Ceci est la documentation officielle de **Boosting Creator**.

Boosting Creator fait du vol de voitures un vrai job. Les joueurs ouvrent un laptop, rejoignent la file et reçoivent des contrats par classe : trouver la voiture garée, la forcer et la démarrer aux fils, se débarrasser d'un traceur GPS et d'un gang armé, puis la livrer à un acheteur, effacer le VIN pour la garder, la désosser dans une casse, ou la ranger dans leur propre garage pour la vendre plus tard. Tout se configure en jeu depuis un seul menu admin, sans redémarrage.

<CardGroup cols={2}>
  <Card title="Boutique" icon="cart-shopping" href="https://fivem.jaksam-scripts.com/">
    Achète ou consulte le script sur la boutique jaksam.
  </Card>

  <Card title="Démonstration" icon="play" href="https://youtu.be/5A-XnFG2Pw0">
    Regarde la démonstration complète sur YouTube.
  </Card>

  <Card title="Langues prises en charge" icon="language">
    Anglais, Allemand, Espagnol, Français, Italien
  </Card>
</CardGroup>

## Ce qu'il fait

<CardGroup cols={2}>
  <Card title="Contrats par classe" icon="ranking-star">
    Classes D à S débloquées avec la réputation, chacune avec ses propres véhicules, sa paie, son temps limite, son minimum de policiers et ses risques.
  </Card>

  <Card title="Vol et traceur" icon="satellite-dish">
    Force la portière, démarre aux fils avec un mini-jeu, puis pirate le traceur GPS pendant que la police suit ses pings.
  </Card>

  <Card title="Gardes et poursuite par un gang" icon="user-ninja">
    Des gardes armés autour de la voiture et des voitures de poursuite avec des tireurs une fois qu'elle est volée.
  </Card>

  <Card title="Fixers" icon="envelope">
    Des acheteurs avec un nom qui écrivent par e-mail, demandent une voiture sans une rayure, une repeinte ou du tuning, et font plus confiance au voleur à chaque job.
  </Card>

  <Card title="Équipes" icon="users">
    Jusqu'à 4 joueurs partagent un contrat, avec la paie partagée et un bonus pour l'équipe.
  </Card>

  <Card title="Garages et porte-voitures" icon="warehouse">
    Range les voitures volées dans un garage de 6 places et vends-les une par une ou toutes ensemble sur un porte-voitures.
  </Card>
</CardGroup>

## Documentation

<CardGroup cols={2}>
  <Card title="Installation" icon="download" href="/fr/boosting-creator/installation">
    Installe Boosting Creator et fais-le tourner sur ton serveur.
  </Card>

  <Card title="Guides" icon="book-open" href="/fr/boosting-creator/guides/how-it-works">
    Fonctionnement d'un contrat, classes, lieux, fixers, équipes, garages et police.
  </Card>

  <Card title="FAQ" icon="circle-question" href="/fr/boosting-creator/faq">
    Questions fréquemment posées.
  </Card>

  <Card title="Référence développeur" icon="code" href="/fr/boosting-creator/editable-files">
    Fichiers modifiables, hooks et exports pour les développeurs.
  </Card>
</CardGroup>

## Frameworks pris en charge

<CardGroup cols={3}>
  <Card title="ESX" icon="code" href="/fr/boosting-creator/installation">
    Paie sur n'importe quel compte, voitures au VIN effacé enregistrées dans `owned_vehicles`.
  </Card>

  <Card title="QBCore" icon="code" href="/fr/boosting-creator/installation">
    Voitures au VIN effacé enregistrées dans `player_vehicles`, paie de société via qb-banking ou qb-management.
  </Card>

  <Card title="Qbox" icon="code" href="/fr/boosting-creator/installation">
    Fonctionne avec qbx_core via la version QBCore.
  </Card>
</CardGroup>
