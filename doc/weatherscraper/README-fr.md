# WeatherScraper — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour WeatherScraper 0.1.135 (octobre 2026). Si ce guide et l'application ne disent pas la
même chose, c'est l'application qui a raison.

---

## 1. Ce qu'est WeatherScraper

WeatherScraper affiche des **prévisions à 14 jours** pour les villes de votre choix. Il n'a pas de
prévisions à lui et ne nomme aucun site météo : c'est **vous** qui lui dites où lire.

- **Une page de prévisions que vous collez :** l'adresse d'une page de prévisions sur plusieurs
  jours, d'un site en qui vous avez confiance. L'application lit son tableau de jours.
- **Un service de prévisions que vous configurez :** l'adresse d'une API de prévisions que vous avez
  le droit d'utiliser, interrogée pour une ville par ses coordonnées.

Une ville peut avoir les deux : une page qui change de mise en page ne vous laisse pas sans
prévisions. La source de chaque prévision est toujours nommée à l'écran, par l'hôte que vous avez
saisi.

Une nouvelle installation est vide : aucune ville, aucune adresse. Un court assistant aide à les
renseigner.

---

## 2. Premier démarrage

L'assistant demande, dans l'ordre :

1. Quelles **sources** utiliser : des pages collées, un service de prévisions, ou les deux.
2. Les **adresses** du service, s'il y en a : l'adresse des prévisions, et l'adresse de géocodage qui
   sert à trouver une ville par son nom. Laissez un champ vide pour le passer ; tout se change plus
   tard dans les [Paramètres](app:settings).
3. Votre **première ville**.
4. Au besoin, votre **SyncHub** ([section 9](#9-synchub)).

Rien n'est enregistré avant de toucher *Commencer*.

---

## 3. Ajouter des villes

Ouvrez le menu et touchez **+ Ajouter une ville**.

- **Par son nom :** tapez au moins deux lettres ; les lieux correspondants s'affichent avec leur
  région. Un toucher ajoute la ville. Il faut pour cela une adresse de géocodage dans les réglages.
- **Depuis une page** (*Outils → Extraire d'une page*, marqué expérimental) :
  1. Collez l'**adresse** de la page de prévisions sur plusieurs jours du site (pas sa page
     d'accueil) et touchez **Analyser**. L'application récupère la page une fois.
  2. Jusqu'à trois tableaux candidats sont présentés en lignes de prévision, chacun avec une
     confiance : *Ressemble à des prévisions*, *Incertain — vérifiez l'aperçu*, *Probablement faux*.
     *Ce n'est pas le bon tableau ?* montre le suivant.
  3. L'aperçu indique les chiffres du jour trouvés (pluie, vent, soleil) et si le site a des **pages
     par jour**, qui donnent les heures d'un jour quand vous l'ouvrez.
  4. Nommez la ville et touchez **Ajouter la ville**. Si le nom correspond à un lieu, ses coordonnées
     sont gardées : le service de prévisions prend le relais si la page cesse de fonctionner.

L'extracteur respecte le `robots.txt` du site, s'identifie honnêtement et va chercher rarement. Si
une page est construite en JavaScript ou refuse la requête, il le dit. *Avancé* permet d'écrire les
sélecteurs à la main. Les conditions du site sont à vous de les respecter.

Dans le menu, chaque ville a un **cœur** (vos favorites, montrées aussi sur la page d'accueil du hub),
une poignée pour la déplacer, et **×** pour la retirer (ses prévisions enregistrées sont supprimées).

---

## 4. Lire les prévisions

L'écran d'accueil montre la ville sélectionnée. **Balayez sur le côté** ou passez par le menu pour
changer de ville.

- **Trois vues**, depuis le menu ⋮ : **Maintenant**, **7 jours** (par défaut, des cartes détaillées)
  et **14 jours** (une liste dense). Au-dessus des deux listes, un **graphique des températures**
  montre les maximales au-dessus des minimales.
- Chaque jour se lit : jour et date, une illustration, min / max, puis condition · risque de pluie ·
  millimètres · vent. Un chiffre que la source n'a pas donné s'affiche **—** : l'application n'en
  invente jamais.
- **La ligne d'état** est toujours là : l'âge des prévisions, la source dont elles viennent (l'hôte
  que vous avez saisi) et le dernier échec si une actualisation a échoué. Un échec ne retire jamais
  les prévisions ; elles restent, avec leur âge.
- Touchez un jour pour son **détail** : les heures quand la source les a, l'humidité, et les
  catégories d'alerte du jour.
- **Actualiser :** tirez vers le bas, ou l'icône d'actualisation dans l'en-tête.
- La **barre d'actions** propose *Partager* (une image des prévisions) et, pour une ville tirée d'une
  page, *Ouvrir la page source*.

### 4.1 Une ville à deux sources

Quand une ville a une page et des coordonnées, **Comparer les sources** (dans les *Paramètres*)
affiche une page par source plus une page **Moyenne** (températures moyennes, la pire condition des
deux). Sinon, le réglage **Source préférée** décide quelle source est utilisée d'abord ; l'autre
prend le relais quand la première échoue.

---

## 5. Actualisation

- Chaque matin à 7 h, l'application actualise toutes vos villes.
- Quand vous ouvrez une ville dont les prévisions ont plus de 30 minutes, elle l'actualise.
- **Intervalle d'actualisation** (désactivé par défaut) ajoute une actualisation toutes les 1, 3, 6
  ou 12 heures. Vous pouvez réserver les actualisations en arrière-plan au Wi-Fi.
- Au plus deux requêtes par actualisation pour une ville tirée d'une page (la liste, puis la page du
  jour), avec des pauses croissantes après des échecs. Un site n'est jamais martelé.

---

## 6. Alertes et avertissements officiels

### 6.1 Les alertes tirées de vos prévisions

*Paramètres → Notifications → Alertes* (désactivé par défaut) surveille **aujourd'hui et demain**
dans vos prévisions enregistrées et vous prévient une fois par ville, jour et type quand l'un de six
phénomènes est attendu : **gel**, **chaleur**, **forte pluie**, **vent fort**, **neige** ou
**orage**. La **sensibilité** (*Faible*, *Normale*, *Élevée*) déplace les seuils ; chaque type peut
être désactivé, chaque ville aussi. Une ville tirée d'une page ne donne en général que températures
et conditions : les alertes de pluie et de vent viennent surtout du service de prévisions. Ces
alertes sont calculées sur le téléphone à partir de vos propres prévisions : elles ne sont pas
officielles.

### 6.2 Les avertissements officiels

Si vous saisissez une **adresse de flux d'alertes** (un flux d'avertissements officiels au format CAP,
*Paramètres → Adresse de l'API*), l'écran des prévisions montre les avertissements qui couvrent la
ville, cités tels qu'émis, et peut les notifier. L'application n'est pas un canal d'alerte : elle
s'actualise à son propre rythme, la page de l'émetteur fait donc foi. Hors de la zone du flux,
l'application n'affiche rien plutôt que « aucun avertissement ».

---

## 7. Les réglages des sources

Dans les [Paramètres](app:settings) :

- **Modèle de prévision :** *Automatique* laisse le service choisir ; cinq modèles nommés peuvent être
  choisis à la place. **Modèle par ville** le remplace pour une ville. Un interrupteur peut dessiner
  l'écart entre modèles sur le graphique.
- **Source préférée** et **Comparer les sources** ([section 4.1](#41-une-ville-à-deux-sources)).
- **Adresse de l'API :** les adresses des prévisions, du géocodage et du flux d'alertes, chacune vide
  jusqu'à ce que vous la remplissiez.
- **Intervalle d'actualisation** et données mobiles ([section 5](#5-actualisation)).

---

## 8. Widget et voiture

- **Widget :** placez-le sur l'écran d'accueil et choisissez une ville et une vue ; sa taille décide
  de ce qu'il montre. Il affiche les prévisions enregistrées et ne va jamais les chercher lui-même.
- **En voiture :** téléphone relié à l'écran d'une voiture, choisissez une ville, puis lisez
  aujourd'hui et les jours suivants, avec la source et l'âge dans l'en-tête. Les alertes restent sur
  le téléphone.

---

## 9. SyncHub

Si vous faites tourner un **SyncHub** à la maison, l'application peut partager avec lui ses villes,
ses cœurs et ses réglages.

1. Ouvrez **SyncHub** en bas du menu. L'application cherche le hub sur votre réseau, ou vous tapez
   son adresse.
2. Dans l'interface web du hub, ouvrez **Paramètres → Appareils → Associer un appareil** et scannez
   le code QR avec l'application.

- **Fiabilité** (dans le menu) montre, pour chaque ville dotée d'un capteur de température déclaré
  sur le hub, l'écart entre les prévisions de chaque source et ce que le capteur a mesuré, selon le
  nombre de jours à l'avance, sur 30, 90 ou 365 jours. Les premiers chiffres arrivent après environ
  une semaine.
- *Tout renvoyer*, sur l'écran de synchronisation, renvoie les données de l'application si le hub les
  a perdues.

---

## 10. Quand quelque chose ne va pas

- **« Cette page semble être construite en JavaScript » :** l'application ne lit que ce que la page
  envoie ; essayez une autre page du site, ou ajoutez la ville par son nom.
- **« Le fichier robots.txt de cette page interdit l'accès automatisé » :** le site demande aux
  robots de ne pas lire cette page ; l'application obéit. Choisissez une autre source.
- **Les prévisions sont anciennes :** la ligne d'état dit pourquoi la dernière actualisation a
  échoué. Les prévisions enregistrées restent jusqu'à une actualisation réussie.
- **Un chiffre affiche — :** la source ne l'a pas donné. Ce n'est pas zéro.
- Questions et idées : *Paramètres → À propos → Envoyer un commentaire*.
