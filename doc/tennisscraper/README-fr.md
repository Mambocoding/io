# Tennis Scraper — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour Tennis Scraper 0.1.140 (octobre 2026). Si ce guide et l'application ne disent pas la même
chose, c'est l'application qui a raison.

---

## 1. Ce qu'est Tennis Scraper

Tennis Scraper suit le tennis professionnel en simple — les circuits masculin et féminin — et **vous
prévient quand un match que vous suivez commence**, pendant qu'il se joue et quand il se termine.

- Tout se passe sur votre téléphone : pas de compte, pas de serveur à nous. Les notifications sont
  calculées par le téléphone lui-même.
- L'application ne fournit aucune adresse de données : c'est **vous** qui saisissez l'adresse de la
  source que vous utilisez ([section 8](#8-source-de-données-et-état)). D'ici là, les écrans restent
  vides et le disent.
- Vous suivez des **joueurs**, des **tournois** entiers à partir d'un tour de votre choix, ou un
  **match** précis.
- **Un match, une notification** de chaque sorte, quel que soit le nombre de raisons de le suivre.

---

## 2. Aujourd'hui

**Aujourd'hui** est l'écran d'accueil, fait de blocs que vous choisissez : **matchs**,
**actualités**, **classements** et **calendrier**.

- Le bloc des matchs montre les matchs de vos favoris et ceux que vous suivez sur une seule ligne du
  temps, avec des séparateurs de jour : à venir avec leur heure, **en direct** avec le score et un
  point qui pulse, terminés avec le résultat. Un match entre deux de vos favoris n'apparaît qu'une
  fois.
- Touchez le titre d'un bloc pour ouvrir son écran ; modifiez la page pour ajouter, retirer ou
  réordonner les blocs.
- Le **mode anti-spoiler** (menu ⋮) masque les actualités et tous les scores et *Gagné* / *Perdu* sur
  Aujourd'hui, pour un match que vous regarderez plus tard. Les lignes en direct gardent leur marque
  *LIVE*.
- Tirez vers le bas pour actualiser. Aujourd'hui s'actualise aussi en arrière-plan, et s'ouvre donc
  sur des données fraîches.
- Le menu ⋮ filtre aussi par circuit : **Tous**, ou l'un des deux circuits. Le filtre vaut pour tous
  les écrans et ne change jamais ce qui est téléchargé.

---

## 3. Joueurs et suivi

- **Joueurs** montre vos favoris, groupés par circuit. Tapez dans le champ de recherche pour trouver
  n'importe quel joueur ; l'étoile ajoute ou retire un favori.
- La **cloche** d'un favori le met en sourdine : il reste favori, mais ses matchs ne notifient plus
  (sauf si une autre raison de suivre le match tient toujours).
- **Suivre ce tournoi** (depuis son en-tête dans Matchs ou Calendrier) : choisissez à partir de quel
  tour — tableau final, quarts, demies ou finale. Chaque match de ce tournoi à partir de ce tour
  notifie alors.
- **Suivre ce match** (dans le détail d'un match) : ses alertes arrivent même si vous ne suivez aucun
  des deux joueurs. Le suivi expire de lui-même après le match.

---

## 4. Matchs, calendrier, tableaux, classements

- **Matchs** liste les matchs d'un jour par tournoi, avec qualifiés, catégorie et tour. Touchez un
  match pour son **détail** : joueurs, score par set, tour, et les actions ci-dessous.
- **Calendrier** liste les tournois par semaine ; ouvrez-en un pour son **tableau**, tour par tour.
  *Site officiel* ouvre la page du tournoi quand l'application la connaît.
- **Classements** montre le classement actuel de chaque circuit ; touchez un joueur pour son détail.
- Dans le détail d'un match :
  - **Partager** envoie le match en texte ;
  - **Ajouter au calendrier** (match à venir avec une heure de début) le confie à votre application
    d'agenda ;
  - **Regarder** (en direct ou sur le point de commencer) ouvre le match sur une page de recherche de
    diffusion — seulement si vous avez renseigné une *Adresse de recherche pour regarder* dans les
    [Paramètres](app:settings).

---

## 5. Notifications

[Paramètres](app:settings) → *Notifications* réunit tous les interrupteurs :

- **Alertes de match :** *Bientôt* (activé, avec le délai avant), *Début du match* (activé), *Score en
  direct* (désactivé) et *Résultat* (activé).
- **Chaque jour :** un **résumé quotidien** des matchs de vos favoris, une notification par joueur, à
  l'heure de votre choix ; et un avis quand un tournoi suivi commence.
- **Heures calmes** (désactivées par défaut, 23 h – 8 h une fois activées) : les alertes qui tombent
  dedans sont abandonnées.
- **Joueurs en sourdine** liste les favoris mis en sourdine.

Toucher une notification ouvre le match.

---

## 6. Actualités

Si vous saisissez une **adresse de flux d'actualités** (un flux RSS ou Atom, dans les *Paramètres*),
**Actus** liste les derniers articles, et Aujourd'hui peut montrer *les actualités de vos favoris*.
**Tout marquer comme lu** se trouve dans la barre d'actions. Sans adresse, les actualités sont
entièrement masquées et rien n'est téléchargé.

---

## 7. Widget et voiture

- **Widget :** jusqu'à trois matchs suivis du jour sur l'écran d'accueil — en direct d'abord, puis à
  venir, puis terminés. Un toucher ouvre Aujourd'hui.
- **En voiture :** téléphone relié à l'écran d'une voiture, les alertes de match peuvent être lues à
  voix haute, et les favoris et le programme du jour consultés.

---

## 8. Source de données et état

- *Paramètres → Source de données* choisit d'où viennent les matchs : une source **tableau des
  scores** (sans clé) ou une **liste de rencontres avec clé** (clé requise), chacune par une adresse
  que vous saisissez. Qui saisit une adresse répond des conditions de ce service. Les favoris sont
  gardés par source.
- *Paramètres → État* dit ce que l'application a fait en dernier : la source utilisée, la dernière
  récupération réussie et la dernière échouée, et les caches. C'est là qu'il faut regarder quand une
  notification n'est pas venue.

---

## 9. Sauvegarder l'application

*Paramètres → Sauvegarde et restauration* enregistre vos favoris, vos suivis et vos réglages dans un
fichier, et les restaure sur un nouveau téléphone.

---

## 10. Quand quelque chose ne va pas

- **Une notification n'est pas venue :** vérifiez dans *Paramètres → État* la dernière récupération,
  que l'alerte est activée, que le joueur n'est pas en sourdine, que vous n'étiez pas dans les heures
  calmes, et que le téléphone autorise les notifications et ne met pas l'application en veille.
- **Un score en direct semble bloqué :** le score affiché est le dernier donné par la source ; tirez
  vers le bas pour actualiser.
- **Pas d'actualités :** l'adresse du flux d'actualités est vide, ou le flux n'a pas répondu.
- Questions et idées : *Paramètres → À propos → Envoyer un commentaire*.
