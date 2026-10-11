# SoundMaster — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Español](README-es.md) · [Nederlands](README-nl.md)*

Rédigé pour SoundMaster 0.1.48 (octobre 2026). Si ce guide et l'application ne disent pas la même
chose, c'est l'application qui a raison.

---

## 1. Ce qu'est SoundMaster

SoundMaster est un **sonomètre** : il montre, en décibels, le niveau sonore autour de votre
téléphone. Il **enregistre** aussi le son quand vous le lui demandez.

Il promet ce qu'un téléphone peut tenir, et rien de plus :

- **Étalonné** face à un vrai sonomètre, une mesure est juste à environ **±3 dB** près. Avec la
  valeur de départ, elle peut s'écarter d'environ **±10 dB**.
- Deux mesures sur le même téléphone se comparent bien (environ ±3 dB), même sans étalonnage.
- La plage utile va d'environ **30 à 95 dB**.

Il répond à *« cette pièce est-elle bruyante ? »*, jamais à *« est-ce contraire à une
réglementation ? »* : ce n'est pas un instrument de classe 1 ou 2. *Paramètres → À propos* en donne
l'énoncé complet.

---

## 2. Premier démarrage

SoundMaster a besoin du **microphone**. Il ne le demande jamais de lui-même au lancement : Mesure
affiche une phrase et un bouton **Autoriser l'accès au microphone**. Si vous avez refusé
définitivement, Mesure le dit et propose d'ouvrir les paramètres système.

Le microphone n'est utilisé que tant que l'application est à l'écran. Rien n'est mesuré ni
enregistré en arrière-plan.

---

## 3. Mesurer

**Mesure** est le premier écran.

- L'**aiguille** montre le niveau actuel ; le grand nombre est le même niveau.
- Les deux **repères** de l'arc, *Min* et *Max*, retiennent le niveau le plus bas et le plus haut de
  l'aiguille depuis l'ouverture de l'application ou depuis la dernière réinitialisation.
- L'**arc** passe du vert au rouge quand le niveau monte (rouge à partir de 85 dB).
- Sous le nombre, un son du quotidien d'un niveau voisin donne l'échelle.
- La ligne sous le nombre dit comment le niveau est calculé : *pondéré A* ou *non pondéré*,
  *rapide* ou *lent* ([section 6](#6-les-réglages-qui-changent-la-mesure)).

Certains états **ne sont pas des niveaux**, et l'application ne les montre jamais comme des nombres :

- **Saturation** — le son est trop fort pour le microphone ; le vrai niveau est plus haut que tout ce
  qui s'affiche.
- **Aucun signal** — le microphone ne livre que du silence pur (souvent, une autre application le
  tient).
- *sous la plage utile* — une pièce calme, sous environ 30 dB : le nombre reste, mais fiez-vous-y
  moins.

### 3.1 Une mesure : mesurer un moment, puis enregistrer

La **barre d'actions** en bas agit sur la mesure en cours :

1. **Démarrer** (la petite icône de graphique) lance une mesure ; le même bouton l'arrête.
2. Pendant une mesure, **Cette mesure** montre son niveau le plus bas et le plus haut et son
   **Leq** (l'énergie moyenne sur la mesure), avec un tracé des 60 dernières secondes.
3. **Enregistrer la session** garde le résultat dans l'**Historique**. *Réinitialiser la mesure*
   efface la mesure et les repères. **Partager** envoie la lecture actuelle en texte.

Quitter l'application met la mesure en pause ; elle reprend à votre retour. Changer la pondération
fréquentielle, ou un changement de source du microphone, termine la mesure, prête à être
enregistrée.

### 3.2 L'alerte

Au-dessus du **seuil d'alerte** (85 dB sauf si vous le changez), Mesure devient rouge et indique le
dépassement. Une **alerte sonore** (un bip court) peut être activée ; elle est désactivée par défaut
car le microphone du téléphone entend le bip. L'alerte ne vaut que ce que vaut l'étalonnage derrière
elle.

---

## 4. Spectre

**Spectre** découpe le son en dix bandes d'octave, de 31,5 Hz à 16 kHz, et montre la bande
dominante. Les bandes sont **relatives** : elles disent quelle partie du son est la plus forte,
jamais un niveau en dB par bande. *Figé* dans le menu ⋮ fige l'image ; *En direct* la relance.

---

## 5. Enregistrer

Le bouton rond **Enregistrer**, sur **Enregistrement** et sur Mesure quand aucune mesure n'est en
cours, démarre un enregistrement ; **Pause** et **Reprendre** sont à côté.

- Les enregistrements sont listés du plus récent au plus ancien, avec leur durée et leur taille, et
  des marques *saturé* et *en pause*. Écoutez-en un sur place.
- Sélectionnez un enregistrement pour la barre d'actions : **supprimer**, **partager**,
  **renommer** et **télécharger** (une copie dans le dossier de votre choix).
- Enregistrer ne change pas la mesure : le sonomètre continue de mesurer.
- Les enregistrements restent sur le téléphone. Ils ne font pas partie de la sauvegarde de
  l'application, et un enregistrement s'arrête quand l'application quitte l'écran.

### 5.1 Transcrire un enregistrement

**Transcrire**, dans la barre d'actions d'Enregistrement, transforme la parole d'un enregistrement
en texte **sur le téléphone**, avec la reconnaissance vocale du système. Rien n'est envoyé nulle
part. Il faut Android 13 ou plus récent et un téléphone dont la reconnaissance fonctionne hors
ligne ; si votre langue n'est pas installée, l'écran propose de la télécharger depuis le système.
La transcription peut être copiée ou partagée, et peut contenir des erreurs.

---

## 6. Les réglages qui changent la mesure

Dans les [Paramètres](app:settings) → *Mesure* :

- **Pondération fréquentielle :** *Pondéré A* (par défaut, proche de l'oreille) ou *Non pondéré*.
- **Pondération temporelle :** *Rapide (125 ms)*, par défaut, suit vite les changements ; *Lent
  (1 s)* calme l'aiguille.
- **Seuil d'alerte** et **Alerte sonore** ([section 3.2](#32-lalerte)).
- **Démarrer une mesure à l'ouverture :** une mesure commence d'elle-même à la première lecture
  après le lancement.
- **Étalonnage** ([section 7](#7-létalonnage)).
- **Niveaux typiques :** des sons du quotidien et leur niveau habituel, la liste à laquelle Mesure
  compare.

---

## 7. L'étalonnage

Chaque microphone de téléphone est différent. L'**étalonnage** ajoute un décalage, en dB, à toutes
les mesures.

1. Placez SoundMaster à côté d'un **vrai sonomètre**, au même endroit, avec un son stable.
2. Ouvrez *Paramètres → Mesure → Étalonnage* et ajustez le décalage jusqu'à ce que les deux
   affichent la même chose.

*Utiliser la valeur de départ* revient à +110 dB. Une autre application de téléphone n'est pas une
référence : elle vérifie seulement que rien n'est grossièrement faux. Chaque session enregistrée
garde le décalage avec lequel elle a été mesurée.

---

## 8. Historique

L'**Historique** liste les sessions enregistrées, de la plus récente à la plus ancienne : date,
durée, Leq, niveau le plus bas et le plus haut, crête, pondérations, décalage et source du
microphone. Une session saturée marque ses chiffres : ce sont des planchers, pas des niveaux.
Sélectionnez des sessions pour les supprimer ou les partager.

---

## 9. Sauvegarder l'application

*Paramètres → Sauvegarde et restauration* enregistre les réglages et l'historique des sessions dans
un fichier (jamais l'audio), et les restaure.

- La **sauvegarde automatique** produit ce fichier chaque jour.
- Si vous avez un SyncHub, la sauvegarde peut aussi être gardée **sur le hub** : associez depuis
  l'écran de sauvegarde, avec le code que le hub affiche. Cette association n'ouvre que les
  sauvegardes de SoundMaster, rien d'autre. C'est la seule fois où l'application utilise le réseau.

---

## 10. Quand quelque chose ne va pas

- **« Le microphone n'a pas pu être ouvert » :** une autre application le tient peut-être, ou le
  téléphone refuse ce type de capture. Fermez l'autre application et revenez à SoundMaster.
- **Aucun signal** alors que la pièce n'est pas silencieuse : une autre application ou un appel tient
  le microphone.
- **« Vos paramètres étaient endommagés et ont été réinitialisés » :** l'application est repartie de
  zéro, avec le décalage de départ. **Vos sessions et enregistrements sont intacts** ; étalonnez à
  nouveau.
- Questions et idées : *Paramètres → À propos → Envoyer un commentaire*.
