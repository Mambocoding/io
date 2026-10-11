# FlightScraper — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour FlightScraper 0.1.79 (octobre 2026). Si ce guide et l'application ne disent pas la même
chose, c'est l'application qui a raison.

---

## 1. Ce qu'est FlightScraper

FlightScraper surveille **un aéroport** et tient un **journal de ses mouvements** : chaque
atterrissage et chaque décollage qu'il observe, avec indicatif, immatriculation, type d'appareil,
exploitant et heure. Des **règles de surveillance** peuvent vous prévenir quand un appareil qui vous
intéresse arrive.

- Il lit des **positions ADS-B** — ce que les appareils diffusent eux-mêmes — et non des horaires.
  C'est pourquoi il voit aussi des vols qu'aucun horaire ne liste : militaires, gouvernementaux,
  convoyages, déroutements ou vols d'essai.
- Un mouvement est une **déduction** à partir de positions ; chacun porte donc sa confiance :
  *observé*, *déduit* ou *incertain*. Un champ manquant s'affiche **—**, jamais deviné.
- Il ne montre que ce qui est diffusé autour d'un aéroport. Ce n'est ni un suivi de vols ni un outil
  de surveillance.

L'application ne nomme aucun service de données : c'est **vous** qui lui donnez l'adresse d'un flux.

---

## 2. Bien démarrer

1. **Choisissez votre aéroport :** *Aéroports* dans le menu → cherchez par nom, ville ou code. Le
   répertoire d'aéroports est livré avec l'application et marche hors ligne ; il remplit pour vous
   coordonnées, altitude et fuseau horaire. Réglez le **rayon** (jusqu'où regarder autour de
   l'aéroport, en km). Plusieurs aéroports peuvent être enregistrés ; un seul est surveillé.
2. **Saisissez un flux :** [Paramètres](app:settings) → *Flux*. Collez l'adresse d'un flux ADS-B que
   vous avez le droit d'utiliser (un agrégateur communautaire, ou votre propre récepteur). Si le flux
   prend un cercle, utilisez `{lat}`, `{lon}` et `{radius_nm}` : l'application les remplit.
   **Tester** interroge une fois et dit combien d'appareils sont revenus.
3. Attendez deux interrogations : la **première ne fait qu'enregistrer ce qui est déjà là** ; les
   mouvements apparaissent à partir de la deuxième.

---

## 3. Le journal des mouvements

**Mouvements** est l'écran d'accueil : du plus récent au plus ancien, groupés par jour.

- Chaque ligne : une flèche (arrivée ou départ), l'heure locale, l'indicatif, l'indicatif de type et
  sa description, l'immatriculation, les règles correspondantes, et une marque de confiance.
- Le menu ⋮ filtre **Arrivées / Départs / Tous**, **affiche ou masque les non correspondants**, trie
  et actualise. La loupe cherche dans le journal.
- **La ligne d'état** au-dessus de la liste dit quand a eu lieu la dernière interrogation réussie et
  combien d'appareils étaient dans le cercle, ou pourquoi la dernière a échoué. Un échec ne retire
  jamais rien.
- Touchez un mouvement pour son **détail** : identité, heures, confiance avec une phrase qui
  l'explique, règles correspondantes, résumé de la trajectoire, et **cet appareil ici** — combien de
  fois il est déjà venu.
- La barre d'actions du détail : **Partager** (en texte), **Ouvrir à l'extérieur** dans le suivi de
  votre choix ([section 7](#7-liens-vers-un-suivi-de-vols)), **Supprimer**.

---

## 4. En direct et Carte

- **En direct** liste les appareils dans le cercle en ce moment, avec distance et altitude,
  actualisés tant que l'écran est ouvert. Sa section **Attendu** montre les appareils qui
  s'approchent de l'aéroport — une prévision, signalée comme telle, donnée en fourchette, et qui
  disparaît quand elle ne tient plus.
- **Carte** dessine les mêmes appareils là où ils sont, autour de l'aéroport et de son cercle. Un fond
  de carte n'apparaît que si vous saisissez une adresse de tuiles dans *Paramètres → Source des
  tuiles* ; la carte fonctionne sans.

En direct et Carte n'interrogent que tant qu'ils sont à l'écran.

---

## 5. Règles de surveillance et notifications

Les **règles de surveillance** décident quels mouvements comptent pour vous.

- Une règle combine des critères : un **type** exact (`A332`), une **famille de types** (un préfixe),
  **militaire**, un **préfixe d'indicatif**, une **immatriculation**, des mots dans la
  **description** ou l'**exploitant**, une **première visite** de cet appareil ou de ce type, un code
  **transpondeur**. *Tous* ou *l'un* d'eux doivent être vrais.
- Choisissez arrivées, départs ou les deux, et une importance. Essayez une règle sur le journal avant
  qu'elle n'alerte : l'écran montre à quels mouvements passés elle aurait correspondu.
- Les **notifications** restent désactivées tant que vous ne les activez pas (*Paramètres →
  Notifications*). Vous êtes prévenu **une fois** par appareil, sens et jour, quel que soit le nombre
  de règles qui correspondent.
- Les **heures calmes** (22 h – 7 h à l'aéroport par défaut) retiennent les notifications jusqu'au
  matin ; une règle de haute importance peut les ignorer.
- Une règle peut aussi vous prévenir quand un appareil correspondant **approche**, avant qu'il ne se
  pose.

---

## 6. Interrogations : à quelle fréquence l'application regarde

- Tant qu'En direct, Carte ou Veille active est ouvert : toutes les minutes par défaut (jamais plus
  souvent que toutes les 30 secondes). Après des échecs, l'application attend plus longtemps — 1, 2,
  4, puis 8 minutes.
- En arrière-plan : environ toutes les 15 minutes, ce qui attrape encore une arrivée, jusqu'à 15
  minutes en retard.
- **Programmation des sondages** (*Paramètres → Notifications*) : pendant les heures de votre choix,
  l'arrière-plan interroge plutôt par courtes rafales.
- **Veille active :** le temps d'une soirée, continuez d'interroger au rythme du premier plan écran
  éteint, pour une durée que vous fixez. Une notification s'affiche tant qu'elle tourne, avec un
  bouton *Arrêter*.

---

## 7. Liens vers un suivi de vols

FlightScraper ne nomme aucun suivi de vols. Dans *Paramètres → Liens*, ajoutez les modèles d'adresse
des suivis que vous utilisez, avec des emplacements que l'application remplit depuis le mouvement
(immatriculation, indicatif, code hexadécimal…). Le premier lien est celui d'*Ouvrir à
l'extérieur* par défaut. L'application ne va jamais chercher ces adresses elle-même.

---

## 8. Horaires (expérimental)

*Outils → Horaires* affiche le tableau des arrivées et départs publié par l'aéroport surveillé, lu
depuis des pages dont vous collez les adresses. Il reste **à côté** du journal, jamais dedans : rien
de ce qu'il lit ne devient un mouvement ni ne déclenche d'alerte. Les lignes que le journal a
probablement vues sont signalées.

---

## 9. Vos données

- *Paramètres → Données → Sauvegarde et restauration* enregistre le journal, les aéroports, les
  règles, les liens et les réglages dans un fichier, et les restaure.
- *Paramètres → Journal* règle combien de temps les mouvements sont gardés (pour toujours par défaut)
  et **exporte le journal** en fichier tableur (CSV).

---

## 10. Quand quelque chose ne va pas

- **« Aucun flux configuré » :** saisissez une adresse de flux ([section 2](#2-bien-démarrer)).
- **« Le flux limite actuellement les requêtes de cette application » :** le flux demande à
  l'application de ralentir ; elle espace d'elle-même. Choisissez un intervalle plus long si cela se
  répète.
- **Rien n'apparaît après la première interrogation :** c'est normal — les mouvements commencent à la
  deuxième.
- **Un mouvement dit *incertain* :** la trajectoire avait des trous ; l'application dit ce qu'elle a
  vu, rien de plus.
- **Les notifications n'arrivent pas :** vérifiez qu'elles sont activées dans l'application,
  autorisées par le téléphone, et que vous n'êtes pas dans les heures calmes. L'économiseur de
  batterie du téléphone peut retarder les interrogations en arrière-plan : les *Paramètres* ont une
  ligne pour en exempter l'application.
- Questions et idées : *Paramètres → À propos → Envoyer un commentaire*.
