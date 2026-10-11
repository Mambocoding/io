# NotesManager — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour NotesManager 0.1.34 (octobre 2026). Si ce guide et l'application ne disent pas la même
chose, c'est l'application qui a raison.

---

## 1. Ce qu'est NotesManager

NotesManager garde trois sortes de notes sur votre téléphone :

- les **notes** — du texte libre, en Markdown si vous le souhaitez ;
- les **listes de contrôle** — des éléments à cocher ;
- les **listes de tâches** — des éléments avec une échéance et, si vous voulez, un rappel.

Vos notes vivent sur le téléphone. Si vous faites tourner un **SyncHub** à la maison, elles voyagent
aussi vers vos autres appareils par son intermédiaire
([section 7](#7-synchroniser-avec-votre-synchub)) ; sans hub, l'application fonctionne exactement de
la même façon.

---

## 2. Écrire une note

- Touchez **+** : une nouvelle note s'ouvre, prête à recevoir du texte. Pas de type à choisir, pas
  de bouton Enregistrer.
- Ce que vous tapez est **enregistré au fil de l'eau**, et encore au moment où vous quittez
  l'application. La barre de titre indique quand la note a été enregistrée.
- Le titre est facultatif : sans titre, c'est la première ligne de la note qui s'affiche.
- Un texte partagé depuis une autre application (*Partager → NotesManager*) devient une nouvelle
  note.

### 2.1 Listes de contrôle et listes de tâches

- Dans le menu ⋮ d'une note, **Convertir** la transforme en **Liste de contrôle** ou en **Liste de
  tâches**, et inversement. Chaque ligne d'une note devient un élément ; les éléments redeviennent
  des lignes. Convertir une liste de tâches en autre chose supprime ses échéances et rappels, et
  l'application le demande avant.
- Ajoutez un élément dans la dernière ligne et validez ; le champ reste ouvert pour le suivant.
- Faites glisser un élément par sa poignée pour le déplacer ; balayez-le pour le retirer (avec
  *Annuler*).
- Le menu ⋮ peut masquer les éléments cochés ou tous les décocher.
- Dans une liste de tâches, un élément reçoit une puce **échéance**, puis une puce **rappel** : à
  l'heure du rappel, une notification montre l'élément ; la toucher ouvre la note. Le premier rappel
  demande l'autorisation d'afficher des notifications.

---

## 3. Retrouver ses notes

- **Toutes les notes** affiche vos notes en cartes ou en liste (le menu ⋮ bascule). Les notes
  **épinglées** viennent en premier.
- **Balayez** une carte vers la droite pour l'épingler, vers la gauche pour l'archiver. Un balayage
  ne supprime jamais.
- **Triez** par dernière modification, création, titre, ou votre propre ordre dans un libellé.
- **Rechercher** (la loupe) parcourt titres, textes et éléments au fil de la frappe — notes
  archivées comprises. Les accents ne comptent pas : *ete* trouve *été*. Restreignez à **Corps** ou
  **Éléments**.

### 3.1 Libellés

Une note peut porter plusieurs **libellés**. Ajoutez-en un depuis la note (la puce *+* sous le titre)
ou créez des libellés dans la section **Libellés** du menu. Toucher un libellé dans le menu n'affiche
que ses notes ; un appui long le renomme ou le supprime. Supprimer un libellé garde ses notes.

---

## 4. Sélectionner, archiver, supprimer

- Un **appui long** démarre une sélection ; touchez d'autres notes pour les ajouter. La barre
  d'actions propose alors épingler, archiver, libellés, partager et supprimer pour toutes à la fois.
- **Archiver** retire une note de *Toutes les notes* et des libellés sans la supprimer ; elle reste
  trouvable et modifiable dans **Archives**.
- **Supprimer** envoie les notes à la **Corbeille**. Une note de la Corbeille peut être
  **restaurée**, ou supprimée définitivement.
- La Corbeille garde les notes **30 jours**, puis les supprime. Ce délai est celui du hub : une note
  gardée plus longtemps pourrait revenir à la vie sur vos autres appareils.

---

## 5. Quand deux appareils modifient la même note

NotesManager **ne fusionne jamais en silence deux versions du texte d'une note**.

- Si le texte d'une note a changé sur deux appareils avant qu'ils se synchronisent, **les deux textes
  sont gardés** : le second devient une **Copie en conflit**, affichée juste après l'original. Lisez
  les deux, gardez ce que vous voulez, supprimez l'autre.
- Si une note change sur un autre appareil **pendant que vous tapez**, votre texte est gardé en copie
  en conflit et la note montre le texte de l'autre appareil, avec une ligne disant où est passée
  votre saisie.
- Dans une liste, les éléments se fusionnent un par un : coches, ordre et dates suivent le dernier
  changement ; deux modifications différentes du texte d'un même élément donnent deux éléments.

---

## 6. Vos données : exporter, importer, tout supprimer

Dans les [Paramètres](app:settings) → *Données* :

- **Exporter les notes** enregistre vos notes en un lot de fichiers Markdown (et les listes de tâches
  dans le format courant des tâches d'agenda) que d'autres applications savent ouvrir.
- **Importer des notes** lit l'export d'une autre application de notes : un zip contenant un fichier
  JSON par note. L'application montre ce qu'elle a trouvé avant d'importer quoi que ce soit ;
  libellés, épingles et notes archivées sont conservés.
- **Supprimer toutes les notes** efface chaque note, libellé et élément de ce téléphone, après que
  vous avez tapé une phrase de confirmation. Vos réglages, le verrouillage et l'association au hub
  restent. Si le téléphone est associé, le hub garde sa copie et la renvoie à la prochaine
  synchronisation : pour que la suppression tienne, dissociez d'abord le hub, ou supprimez les notes
  sur le hub lui-même.

---

## 7. Synchroniser avec votre SyncHub

1. Ouvrez **SyncHub** en bas du menu. L'application cherche le hub sur votre réseau domestique ; si
   elle ne le trouve pas, tapez son adresse.
2. Dans l'interface web du hub, ouvrez **Paramètres → Appareils → Associer un appareil** et
   **scannez** le code QR avec l'application (le bouton *Scanner*). Le scan vérifie exactement le
   certificat du hub.
3. Vos notes partent vers le hub et, dès lors, circulent dans les deux sens.

- **Mode de synchronisation :** *Automatique* se synchronise tout seul, peu après chaque changement
  et en arrière-plan ; *Manuel* attend **Synchroniser maintenant**.
- L'écran de synchronisation montre quand a eu lieu le dernier échange et, par sorte de données,
  combien de changements sont passés dans chaque sens.
- Si le hub reste longtemps injoignable, l'application peut vous prévenir par une notification.
- L'interface web du hub affiche et modifie les mêmes notes.

---

## 8. Confidentialité et verrouillage

- Les notes sont stockées sur le téléphone seulement, et sur votre propre hub si vous en associez
  un. L'application ne se connecte à rien d'autre.
- **Verrouillage de l'application** (*Paramètres*) : NotesManager demande votre empreinte, votre
  visage ou le verrouillage de l'écran à l'ouverture, et après le délai de votre choix. Le
  verrouillage cache l'application ; il ne **chiffre pas** vos notes.

---

## 9. Quand quelque chose ne va pas

- **« Vos paramètres étaient endommagés et ont été réinitialisés » :** l'application n'a pas pu lire
  ses réglages et a recommencé à zéro. **Vos notes sont intactes.** L'association au hub est à
  refaire ; le hub reçoit alors à nouveau vos notes.
- **Une note est marquée *Copie en conflit* :** deux versions de son texte se sont croisées ; voir
  la [section 5](#5-quand-deux-appareils-modifient-la-même-note).
- **Un rappel n'a pas sonné :** vérifiez que les notifications sont autorisées pour NotesManager, et
  que le téléphone lui permet de programmer des alarmes exactes.
- Questions et idées : *Paramètres → À propos → Envoyer un commentaire*.
