# StocksScraper — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour StocksScraper 0.2.175 (octobre 2026). Si ce guide et l'application ne disent pas la même
chose, c'est l'application qui a raison.

---

## 1. Ce qu'est StocksScraper

StocksScraper suit une **liste de favoris** — actions, ETF, matières premières et cryptomonnaies — et
**vous prévient quand l'un d'eux bouge** de ±5 % (ou du seuil de votre choix). C'est un outil
personnel : tout est calculé sur votre téléphone, sans serveur ni compte.

- La **liste de favoris** est gratuite, complète et illimitée.
- Le **portefeuille** — ce que vous possédez, ce que cela vaut, si vous êtes gagnant — est la partie
  premium, un achat unique. Il est visible, avec une étincelle, avant que vous l'ayez.
- Aucune source de prix n'est intégrée : c'est **vous** qui donnez à l'application les adresses des
  sources que vous utilisez.

---

## 2. Sources de données

[Paramètres](app:settings) → *Sources de données* contient une adresse par **rôle**, chacun nommé
d'après la forme de ce qu'il répond : une série de cours sans clé (la source principale), un instantané
de cotation et une série temporelle (toutes deux avec une clé que vous saisissez), une cotation CSV et
un prix de cryptomonnaie. Un rôle sans adresse reste inactif.

- Chaque type d'instrument a sa propre **chaîne de repli** : si la première source échoue, la suivante
  est interrogée. Vous n'avez jamais à choisir à la main.
- *Statut*, sur le même écran, dit quelle source a répondu en dernier et ce que fait la chaîne.
- Sans aucune source, la liste le dit au lieu d'afficher une erreur sur chaque ligne.
- Qui saisit une adresse répond des conditions de ce service.

---

## 3. La liste de favoris

- **Ajoutez** un instrument avec **+** (ou *Rechercher / ajouter* dans le menu) : cherchez par nom
  ou symbole ; les cotations locales sont trouvées aussi.
- **Catégories :** regroupez vos favoris sous vos propres titres, repliez-les, et faites-les glisser
  dans l'ordre voulu (*Réorganiser*).
- Chaque ligne montre le type de l'instrument, son prix et — à votre choix dans le menu ⋮ — ses
  chiffres ou une courbe de tendance. Un **point** dit si le marché est ouvert : un prix vivant ou figé.
- À l'ouverture, l'application montre tout de suite les derniers prix connus, estompés et datés, puis
  les actualise.
- Touchez un instrument pour son **détail** : un graphique des cours sur plusieurs périodes, l'état du
  marché, ses actualités, des liens, et ses propres alertes.
- Le **cœur** d'un instrument choisit s'il apparaît sur la page d'accueil de votre SyncHub.

---

## 4. Alertes

- Une alerte arrive quand un instrument bouge du **seuil** (5 % par défaut) par rapport à la clôture
  précédente. L'application vérifie toutes les heures par défaut, en arrière-plan.
- *Paramètres → Notifications* règle le seuil, la fréquence de vérification, le nombre d'alertes par
  instrument et par jour (une par défaut), une alerte facultative de mouvement **hebdomadaire**
  (désactivée par défaut), et la **Silence nocturne** : une alerte qui tombe dans la plage est montrée
  à sa fin, si elle tient toujours.
- Dans les **Alertes** d'un instrument : son propre seuil, des **niveaux de prix** (une fois franchis,
  ils sonnent une fois), et **Silencieux** pour 1 jour, 1 semaine ou jusqu'à réactivation.
- **Alertes**, dans le menu, répond à *qu'ai-je manqué ?* : toutes les alertes déclenchées sur la
  liste, de la plus récente à la plus ancienne ; le menu ⋮ filtre niveaux de prix ou variations en
  pourcentage.
- Une alerte porte sur la séance du jour et dit quand le mouvement a eu lieu. La toucher ouvre
  l'instrument.

---

## 5. Portefeuille (premium)

- **Positions :** ce que vous détenez, valorisé dans une **devise de référence** (*Paramètres →
  Portefeuille*), avec le gain par ligne et au total, et une courbe de valeur sur la période choisie.
- **Une position, ce sont ses transactions :** ouvrez une position pour ajouter achats, ventes et
  dividendes ; quantité et prix de revient moyen en découlent.
- Des soldes de **liquidités** et des **sous-portefeuilles** (un par compte, par exemple) : le titre
  bascule de l'un à l'autre.
- **Plan d'investissement :** un ordre d'achat permanent — hebdomadaire, mensuel, deux fois par mois
  ou trimestriel — passe ses propres achats aux jours prévus.
- **Import / export :** collez ou choisissez une liste de positions (CSV), ou importez le relevé d'une
  banque — un état des positions ou un journal daté — dont le format est reconnu tout seul.
- Le portefeuille n'est jamais envoyé nulle part, sauf si vous activez *Synchroniser mon
  portefeuille* ([section 7](#7-synchub)).

---

## 6. Actualités et widget

- **Actualités** réunit les articles sur votre liste ; le détail d'un instrument montre les siens.
  Lisez, marquez d'une étoile, gardez pour une lecture hors ligne, ou ouvrez l'original.
- Le **widget** montre votre liste sur l'écran d'accueil, avec les derniers prix connus ; il ne va
  jamais les chercher lui-même.

---

## 7. SyncHub

Si vous faites tourner un **SyncHub** à la maison, l'application garde identiques votre liste, vos
catégories, vos alertes et vos réglages sur plusieurs téléphones et dans l'interface web du hub.

1. Ouvrez **SyncHub** dans le menu. L'application cherche le hub sur votre réseau, ou vous tapez son
   adresse.
2. Dans l'interface web du hub, ouvrez **Paramètres → Appareils → Associer un appareil** et scannez le
   code QR. L'application ne fait confiance au hub qu'une fois l'empreinte de son certificat
   confirmée.

- Le **portefeuille** ne voyage que si vous activez **Synchroniser mon portefeuille** (premium), après
  une confirmation.
- **Tout renvoyer** remplit à nouveau un hub qui a perdu ses données.
- Si le hub reste longtemps injoignable, l'application vous le dit.

---

## 8. Sécurité et sauvegardes

- *Paramètres → Sécurité → Verrouillage de l'application* : protégez toute l'application, ou
  seulement le portefeuille, avec votre empreinte, votre visage ou le verrouillage de l'écran. Le
  verrouillage cache ; il ne **chiffre pas**.
- *Paramètres → Sauvegarde et restauration* enregistre la liste, les alertes et les réglages dans un
  fichier — le portefeuille seulement si vous le cochez — et les restaure. Les clés d'API ne vont
  jamais dans une sauvegarde en clair.

---

## 9. Quand quelque chose ne va pas

- **« Aucune source de données configurée » :** saisissez au moins l'adresse de la source principale
  ([section 2](#2-sources-de-données)).
- **Un prix semble ancien :** le point et la ligne d'âge disent si le marché est fermé ou si la source
  n'a pas répondu ; *Sources de données → Statut* dit quelle source a répondu en dernier.
- **Une alerte n'est pas venue :** vérifiez le seuil et le nombre par jour, si l'instrument est en
  silencieux, la silence nocturne, et que le téléphone autorise les notifications de l'application.
- Questions et idées : *Paramètres → À propos → Envoyer un commentaire*.
