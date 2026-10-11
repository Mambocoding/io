# Gestionnaire de fichiers — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour le Gestionnaire de fichiers 1.2.329 (octobre 2026). Si ce guide et l'application ne disent pas la même
chose, c'est l'application qui a raison.

---

## 1. Ce qu'est le Gestionnaire de fichiers

Le Gestionnaire de fichiers est un explorateur de fichiers pour votre téléphone et votre téléviseur.
Il parcourt le stockage du téléphone, une carte SD ou une clé USB, et les serveurs de votre réseau
domestique ; il copie, sauvegarde et synchronise des dossiers entre tous ces endroits.

- Tout reste sur vos appareils : pas de compte, pas de nuage à nous.
- La base est gratuite et sans publicité. Certaines fonctions font partie de l'offre premium ; elles
  portent une étincelle dorée (voir la [section 13](#13-gratuit-et-premium)).
- Sur un téléviseur, la même application parcourt les mêmes endroits avec la télécommande.

---

## 2. Premier démarrage

1. Un court assistant vous demande d'accepter les conditions d'utilisation, puis de choisir le
   **mode de l'application** et un thème. Le mode se change plus tard dans les
   [Paramètres](app:settings) → *Interface* :
   - **Explorateur de fichiers** (par défaut) s'ouvre sur vos fichiers ;
   - **Visionneuse de photos** s'ouvre sur vos photos, en galerie.
2. Android demande ensuite l'accès à vos fichiers. Choisissez **Autoriser l'accès** pour parcourir
   tout le stockage, ou **Choisir un dossier à la place** pour n'ouvrir qu'un seul dossier.
3. La première fois que vous ouvrez une connexion vers votre réseau domestique, Android peut demander
   l'**accès au réseau local**. Autorisez-le : sans lui, toute connexion à votre réseau finit en délai
   dépassé. Vous pourrez l'activer plus tard dans les autorisations de l'application.

---

## 3. Parcourir

- Le **chemin** en haut est une rangée de puces : touchez-en une pour revenir à ce dossier. Le
  dossier que vous venez de quitter reste en puce estompée, pour y retourner.
- **Affichages :** liste détaillée, grille ou grande grille, depuis le menu ⋮, ou en pinçant la
  liste.
- **Tri :** par nom, date, taille ou type, croissant ou décroissant ; les dossiers peuvent rester en
  tête.
- **Recherche :** touchez la loupe ; les résultats remplacent la liste dès la première lettre. La
  recherche porte sur le dossier courant et ses sous-dossiers ; une icône de la barre de recherche
  l'étend à tout l'appareil.
- **Récents :** l'icône horloge sur la ligne *Stockage interne* du menu montre les fichiers ouverts
  récemment (7 ou 30 jours). *Effacer l'historique récent* oublie la liste propre à l'application.
- **Mémoriser le dernier emplacement** (activé par défaut) rouvre le dernier dossier visité.
- **Écran partagé :** sur un écran large (tablette, ou téléphone en paysage), deux volets se côtoient
  pour copier de l'un à l'autre. Il se désactive dans *Paramètres → Interface*.

### 3.1 Favoris

En haut de votre stockage interne, des tuiles mènent à **Photos**, **Musique** et
**Téléchargements**. Touchez **+ Ajouter** pour épingler un dossier ; un appui long sur une tuile la
retire (seul le raccourci disparaît, jamais le dossier). Chaque connexion et chaque carte SD a ses
propres favoris. Le panneau se replie avec sa flèche, ou disparaît avec *Paramètres → Interface →
Afficher le panneau des favoris*.

---

## 4. Travailler avec les fichiers

- **Sélectionnez** par un appui long, puis touchez d'autres fichiers ; *Tout sélectionner* est dans
  la barre d'actions.
- La **barre d'actions** (la pilule flottante) réunit ce que l'on peut faire de la sélection :
  copier, déplacer, renommer, supprimer, partager, compresser… Sa position (flottante, en haut ou en
  bas) et ses boutons se règlent dans *Paramètres → Interface → Barre d'actions*.
- **Copier et déplacer :** après *Copier* ou *Déplacer*, allez à la destination et collez. Si un nom
  existe déjà, l'application demande avant de toucher à quoi que ce soit : **Remplacer** ou
  **Dupliquer** (`nom (1)`), avec *Pour tous les conflits* pour répondre une seule fois.
- Un collage de plus de trois fichiers continue en arrière-plan, avec sa progression dans une
  notification et dans **Outils → Transferts**.
- **Supprimer :** sur le stockage interne, un fichier supprimé va d'abord dans la **Corbeille**
  ([section 10](#10-libérer-de-lespace-et-la-corbeille)). Sur un partage réseau ou une carte SD
  ouverte par le sélecteur d'Android, la suppression est définitive, et la confirmation le dit.
- Les **propriétés** montrent taille, dates et emplacement ; pour une sélection, la taille totale.
- **Zip :** ouvrez un `.zip` pour le parcourir, l'extraire, ou compressez une sélection en une
  nouvelle archive.
- **Éditeur de texte :** les fichiers texte s'ouvrent dans un éditeur intégré, avec rechercher et
  remplacer.

---

## 5. Photos, documents et médias

- **Visionneuse d'images :** balayez vers la photo suivante ou précédente, pincez ou touchez deux fois
  pour zoomer. Le titre indique quand la photo a été prise. Un toucher masque ou affiche les barres.
- La pilule de la visionneuse réunit **Partager · Modifier · Détails · Utiliser comme… · Diaporama ·
  Imprimer · Supprimer**. Après une suppression, la photo suivante prend sa place.
- **Éditeur de photos :** recadrer, pivoter, retourner et redresser sont gratuits ; redimensionner,
  couleurs, filtres, annotations, détourage et gomme sont premium.
- **PDF :** les fichiers PDF s'ouvrent dans l'application, avec recherche et saut de page. Le
  Gestionnaire de fichiers peut aussi devenir le lecteur PDF du téléphone.
- **Lecteur :** musiques et vidéos se lisent dans l'application, y compris directement depuis un
  partage réseau.
- Un fichier sur une connexion s'ouvre directement dans l'application ; une autre application en
  reçoit une copie temporaire.

---

## 6. Connexions réseau

Le Gestionnaire de fichiers atteint les serveurs de votre réseau domestique comme s'ils étaient des
dossiers du téléphone.

1. Ouvrez le menu, puis **Connexions → Ajouter une connexion**.
2. Choisissez le type : **SMB** (dossiers partagés d'un ordinateur et la plupart des NAS, gratuit), **FTP/FTPS**,
   **SFTP**, **WebDAV** ou **S3** (premium).
3. Saisissez l'adresse du serveur, votre nom d'utilisateur et votre mot de passe, et au besoin un
   dossier de départ. Le mot de passe est enregistré chiffré sur le téléphone.
4. La connexion apparaît dans le menu avec son espace libre. Touchez-la pour la parcourir.

La première fois qu'un serveur présente un certificat inconnu, l'application vous demande de lui
faire confiance ; ensuite, un certificat différent est refusé.

### 6.1 L'espace de fichiers de votre SyncHub

Si vous faites tourner un SyncHub à la maison, son espace de fichiers est une connexion **WebDAV** :
l'adresse du hub, le nom de votre compte comme nom d'utilisateur, et le jeton d'application du hub
comme mot de passe.

---

## 7. Synchronisation de dossiers

Les **tâches** copient des dossiers d'un endroit à un autre, encore et encore, d'un toucher ou selon
un horaire.

1. Ouvrez **Tâches** dans le menu et créez une tâche. L'assistant demande :
   - **Quel type de synchronisation ?** **Sauvegarder** (copie les fichiers nouveaux et modifiés ;
     rien n'est supprimé), **Miroir** (rend la cible identique), **Déplacer**, **Télécharger** ou
     **Bidirectionnel** ;
   - le dossier **source** et le dossier **cible**, sur le téléphone ou sur une connexion ;
   - les options : filtres, conduite en cas de conflit, notifications, exécution automatique ou non.
2. Lancez-la avec le bouton lecture, dans la liste des tâches ou dans le menu. **Lancer toutes les
   tâches**, en bas de la liste, les exécute l'une après l'autre.
3. La page d'une tâche montre sa progression, son dernier résultat et son historique ; on peut la
   mettre en pause, l'arrêter, la modifier ou la désactiver.

Gratuit : une **sauvegarde** manuelle vers le téléphone ou un partage SMB — aussi directement depuis
l'explorateur avec *Sauvegarder vers le réseau…*. Premium : les autres types, les horaires, la
synchronisation en direct et les options avancées.

Une tâche automatique s'exécute toutes les 1, 3, 6, 12 ou 24 heures, uniquement en Wi-Fi sauf si
vous autorisez les données mobiles, et au besoin seulement pendant la charge.

---

## 8. Envoyer des fichiers à un appareil proche

**Envoyer vers un appareil** échange des fichiers avec les téléphones et ordinateurs du même Wi-Fi,
sans câble ni nuage.

- Pour **recevoir**, ouvrez *Envoyer vers un appareil* et activez **Me rendre visible**. Vous ne
  restez visible que tant que cet écran est ouvert.
- Une offre entrante demande toujours d'abord : **Accepter**, **Refuser** ou **Bloquer**, et où
  enregistrer. Rien n'est reçu avant votre accord.
- Pour **envoyer**, choisissez un appareil dans la liste, puis les fichiers ; ou utilisez *Partager*
  depuis une autre application et choisissez *Partager vers un appareil*.
- Un appareil introuvable s'ajoute par son adresse ou en scannant son code QR.

Les transferts sur le même Wi-Fi ne sont pas chiffrés : utilisez-les à la maison, pas sur un réseau
public.

---

## 9. Partager cet appareil (premium)

Un ordinateur du même Wi-Fi parcourt et télécharge les fichiers du téléphone dans son navigateur web,
sans rien installer.

1. **Connexions → Partager cet appareil**, choisissez le dossier partagé, et décidez si le
   navigateur peut aussi envoyer et supprimer (*Autoriser l'envoi et la suppression depuis le
   navigateur*, désactivé par défaut).
2. **Démarrer le partage :** l'écran affiche une adresse, un code QR et un code PIN à six chiffres.
3. Ouvrez l'adresse sur l'ordinateur et saisissez le code PIN.

Le partage s'arrête avec *Arrêter le partage*, ou de lui-même après 30 minutes sans utilisation.
Après cinq codes faux, il ne répond plus. La connexion n'est pas chiffrée, et l'écran le dit :
utilisez-le seulement à la maison.

---

## 10. Libérer de l'espace et la Corbeille

- **Outils → Libérer de l'espace** range les fichiers volumineux et anciens par catégories. Rien
  n'est présélectionné : vous examinez chaque fichier, puis **Mettre à la corbeille**.
- **Outils → Corbeille** liste ce qui a été supprimé du stockage interne. **Restaurer** remet un
  fichier à sa place ; **Vider la corbeille** supprime tout définitivement.
- Dans *Paramètres → Corbeille*, choisissez si une suppression passe par la Corbeille ou supprime
  directement, et combien de temps la Corbeille garde les fichiers (jusqu'à ce qu'on la vide, ou 5,
  15, 30 ou 90 jours).

---

## 11. Confidentialité : verrouillage et coffre

- **Verrouillage de l'application** (gratuit, *Paramètres → Confidentialité*) : le Gestionnaire de
  fichiers demande votre empreinte, votre visage ou le verrouillage de l'écran à l'ouverture, et
  après le délai de votre choix quand vous le quittez. Son contenu est masqué dans l'écran des
  applications récentes.
- **Coffre** (premium) : un espace privé et chiffré. Les fichiers qu'on y place (*Déplacer vers le
  coffre*) sont chiffrés sur le téléphone et cachés de la galerie et des autres applications. Le
  coffre s'ouvre avec le verrouillage de l'écran.
  - À sa création, l'application affiche un **code de récupération**. Notez-le et gardez-le loin du
    téléphone : c'est le seul moyen d'y revenir si le verrouillage d'écran est retiré, si le
    téléphone est réinitialisé ou si vous changez de téléphone. Personne ne peut le réinitialiser
    pour vous ; sans lui, les fichiers du coffre sont perdus pour de bon.
  - *Enregistrer une copie hors du coffre* écrit une copie déchiffrée d'un fichier en dehors du
    coffre.

---

## 12. Sauvegarder l'application

*Paramètres → Sauvegarde et restauration* enregistre l'application elle-même — connexions, tâches,
favoris, thèmes et réglages — dans un seul fichier chiffré, protégé par une phrase secrète de votre
choix, et la restaure sur un nouveau téléphone.

- La **sauvegarde automatique** produit ce fichier chaque jour, toute seule.
- Si vous avez un SyncHub, la sauvegarde peut aussi être gardée **sur le hub** : associez
  l'application au hub depuis l'écran de sauvegarde. Cette association n'ouvre que les sauvegardes
  du Gestionnaire de fichiers, rien d'autre.

Vos fichiers eux-mêmes ne sont pas dans cette sauvegarde : copiez-les avec une tâche
([section 7](#7-synchronisation-de-dossiers)).

---

## 13. Gratuit et premium

Gratuit, pour de bon : parcourir, les opérations sur les fichiers, les favoris, la galerie, les
visionneuses et le lecteur, la Corbeille et *Libérer de l'espace*, le zip, les connexions SMB, la
sauvegarde manuelle vers SMB ou le téléphone, *Envoyer vers un appareil*, le verrouillage, et la
sauvegarde automatique de l'application.

Premium : les autres types de connexion (FTP/FTPS, SFTP, WebDAV, S3), toute synchronisation au-delà
d'une sauvegarde manuelle, les horaires et la synchronisation en direct, les outils avancés de
l'éditeur de photos, les profils de traitement, le coffre et *Partager cet appareil*.

Une fonction premium est visible partout avec une étincelle dorée ; la toucher ouvre l'écran premium.
Une tâche qui utilise une option premium est sautée, jamais exécutée à moitié.

---

## 14. Quand quelque chose ne va pas

- Les messages d'erreur disent ce qui s'est passé en mots simples. **Détails**, sous un message,
  montre la cause technique, que vous pouvez copier dans un commentaire (*Paramètres → À propos →
  Envoyer un commentaire*).
- **Une connexion dépasse le délai :** vérifiez que l'*accès au réseau local* est autorisé pour
  l'application, que le téléphone est sur le même Wi-Fi que le serveur, et l'adresse du serveur.
- **« Vos paramètres étaient endommagés et ont été réinitialisés » :** l'application n'a pas pu lire
  ses réglages et a recommencé à zéro. Vos fichiers sont intacts ; connexions, tâches et favoris sont
  à refaire, ou à restaurer depuis une sauvegarde ([section 12](#12-sauvegarder-lapplication)).
- **Une tâche s'est arrêtée :** ouvrez-la dans *Tâches* ; sa page dit pourquoi. Les coupures réseau
  passagères reprennent d'elles-mêmes ; une tâche en pause vous attend.
