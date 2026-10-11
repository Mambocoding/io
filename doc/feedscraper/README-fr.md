# FeedScraper — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour FeedScraper 0.1.252 (octobre 2026). Si ce guide et l'application ne disent pas la même
chose, c'est l'application qui a raison.

---

## 1. Ce qu'est FeedScraper

FeedScraper est un **lecteur de flux** : vous vous abonnez aux flux des sites que vous suivez (RSS,
Atom, RDF ou JSON Feed), et leurs nouveaux articles arrivent sur votre téléphone.

- Tout est récupéré et stocké sur le téléphone : pas de compte, pas de serveur à nous.
- Lisez, marquez d'une étoile, gardez pour une lecture hors ligne, cherchez, et recevez les
  nouveautés en arrière-plan.
- Si vous faites tourner un **SyncHub** à la maison, vos flux et vos lectures peuvent vous suivre sur
  d'autres téléphones et dans l'interface web du hub
  ([section 8](#8-synchroniser-avec-votre-synchub)). Sans hub, l'application est un simple lecteur.

---

## 2. Ajouter des flux

- **Ajouter un flux** (dans le menu) : collez l'adresse d'un flux, ou simplement du site — si la page
  propose plusieurs flux, vous en choisissez un. Le titre est repris du flux ; changez-le si vous le
  souhaitez, et choisissez une catégorie.
- **Importer depuis un fichier** (OPML, la liste d'abonnements standard, dans les *Paramètres*) :
  reprend les flux d'un autre lecteur. L'import ne fait qu'ajouter ; il ne supprime ni ne réorganise
  jamais vos flux. **Exporter vers un fichier** fait l'inverse.
- **Extraire un flux d'une page** (*Outils*) : pour un site sans flux, l'application propose une règle
  qui repère les articles dans la page, et l'applique à chaque actualisation. C'est expérimental.

---

## 3. Lire

- **Vues** dans le menu : **Tous les flux**, **Favoris** (articles étoilés), **Enregistrés (hors
  ligne)**, et un résumé **Flux** avec un bouton par flux. Chaque flux et chaque catégorie est aussi
  une vue.
- La liste ne bouge pas pendant que vous lisez : les articles qui arrivent pendant la visite attendent
  derrière une pastille *nouveaux articles* en haut. Défilez jusqu'au bout pour charger les plus
  anciens.
- **Balayez** une ligne pour la marquer lue ou non lue, ou pour l'étoiler. Un **appui long**
  sélectionne un article et la barre d'actions montre ce qu'on peut en faire.
- **Tout marquer comme lu** vide une vue d'un coup.
- Ouvrez un article pour le lire ; balayez ou utilisez les flèches pour le précédent et le suivant. La
  barre d'actions propose étoile, partage, enregistrement hors ligne et ouverture dans le navigateur.
  La taille du texte et l'interligne se règlent.
- La loupe **cherche** dans la vue courante ; un toucher l'étend à tous les flux.
- Sur un écran large, la liste et l'article ouvert se tiennent côte à côte.

---

## 4. Lire hors ligne

**Enregistrer hors ligne** garde un article avec son texte et ses images, lisible sans réseau ;
**Enregistrer le flux hors ligne** le fait pour tous les non-lus d'un flux. Les articles enregistrés
sont dans **Enregistrés (hors ligne)**. Les *Paramètres* montrent la place qu'ils prennent, peuvent
les retirer une fois lus après un délai, et peuvent réserver les images au Wi-Fi.

---

## 5. Organiser ses flux

- **Modifier les flux et les catégories** (dans le menu) réordonne flux et catégories, déplace des
  flux d'une catégorie à l'autre, fusionne ou supprime des catégories.
- Modifier un flux change son adresse, son titre et sa catégorie, le désactive, ou **désabonne**.
  *Masquer les articles dont le titre contient* masque des articles par mot-clé (un terme par
  ligne) ; ils ne sont pas supprimés, et effacer le terme les fait revenir.
- Un **cœur** sur un flux en fait un favori ; avec un hub, le hub s'en sert pour dire ce qui est
  nouveau.
- Un flux qui échoue sans cesse est signalé dans le menu, avec un lien vers son **journal des
  récupérations**. Si l'adresse d'un flux n'existe plus, l'application propose les flux que le site
  annonce désormais.

---

## 6. Actualisation et notifications

- Les flux s'actualisent en arrière-plan, en ne téléchargeant que ce qui a changé et en espaçant les
  flux qui échouent. Les *Paramètres* règlent la fréquence, l'usage des données mobiles, et
  l'actualisation de tous les flux à l'ouverture.
- Tirez vers le bas dans une vue pour l'actualiser tout de suite.
- Les **notifications de nouveaux articles** sont désactivées par défaut et se choisissent flux par
  flux.
- **Supprimer les articles lus plus anciens que** (désactivé par défaut) garde la base de données
  légère.

---

## 7. Réglages et confidentialité

Dans les [Paramètres](app:settings) : **Ouvrir au démarrage** (là où vous en étiez, le résumé des
flux ou vos favoris), affichage, actualisation, notifications, stockage hors ligne, sauvegardes et
verrouillage.

- Les articles sont nettoyés avant d'être affichés : aucun script d'un article ne s'exécute jamais.
- Le **verrouillage** (désactivé par défaut) demande votre empreinte ou le verrouillage de l'écran ;
  il cache, il ne chiffre pas.
- *Sauvegarde et restauration* enregistre vos flux, catégories, états de lecture et réglages dans un
  fichier, et les restaure.

---

## 8. Synchroniser avec votre SyncHub

La synchronisation avec un hub est ce que débloque un achat unique ; tout le reste est gratuit.

1. Ouvrez **SyncHub** dans le menu. L'application cherche le hub sur votre réseau, ou vous tapez son
   adresse.
2. Dans l'interface web du hub, ouvrez **Paramètres → Appareils → Associer un appareil**, et scannez
   le code QR avec l'application.
3. Comparez l'empreinte du certificat quand on vous le demande : l'application ne fait confiance au
   hub qu'une fois que vous l'avez confirmée.

- Flux, catégories, cœurs, états lu et étoilé et réglages circulent alors dans les deux sens ; le hub
  continue de récupérer vos flux pendant que votre téléphone dort.
- Si le certificat du hub change, la synchronisation s'arrête jusqu'à votre décision. Rien n'est
  réapprouvé en silence.
- Si le hub reste longtemps injoignable, l'application vous le dit. Le point du menu montre l'état de
  la synchronisation d'un coup d'œil.

---

## 9. Quand quelque chose ne va pas

- **« … ne s'est pas actualisé — diagnostiquer » :** ouvrez le journal des récupérations du flux ; il
  dit ce que le site a répondu.
- **« … continue de nous refuser » :** le site bloque les lecteurs automatiques ; l'application n'y
  peut rien poliment.
- **Un article n'a pas d'image :** certains sites refusent les images aux applications ; l'article se
  lit quand même.
- **La synchronisation s'est arrêtée après un changement du hub :** comparez la nouvelle empreinte sur
  les pages du hub avant de lui refaire confiance.
- Questions et idées : *Paramètres → À propos → Envoyer un commentaire*.
