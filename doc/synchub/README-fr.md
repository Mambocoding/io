# SyncHub — guide d'utilisation

*[English](README-en.md) · Français · [Deutsch](README-de.md) · [Nederlands](README-nl.md)*

Rédigé pour SyncHub 0.2.216 (octobre 2026). Si ce guide et les pages du hub ne disent pas la même
chose, c'est le hub qui a raison.

---

## 1. Ce qu'est SyncHub

SyncHub est un petit serveur que vous faites tourner **sur votre propre machine** — le plus souvent
un NAS à la maison — pour que les données de vos applications restent chez vous plutôt que dans le
nuage de quelqu'un d'autre.

- Il garde les données de plusieurs applications (flux, météo, bourse, notes) pour **plusieurs
  personnes**, chaque compte étant totalement séparé des autres.
- Il **récupère vos contenus jour et nuit** : un téléphone resté éteint ne rate rien.
- Il offre une **interface web** dans votre navigateur, avec le même contenu que votre téléphone.
- Il **synchronise dans les deux sens** : ce que vous mettez en favori ou marquez comme lu dans le
  navigateur apparaît sur le téléphone, et inversement.

Il est **facultatif** : une application sans hub configuré fonctionne exactement comme avant.

Il **ne s'ouvre jamais à Internet**. Il répond uniquement sur votre réseau domestique. L'atteindre
depuis l'extérieur est votre choix, via un VPN ou votre propre proxy inverse (voir la
[section 12](#12-y-accéder-hors-de-chez-soi)).

---

## 2. Ce qu'il vous faut

- Une machine allumée en permanence qui fait tourner des **conteneurs** (un NAS avec un gestionnaire
  de conteneurs, un petit serveur Linux, un mini-PC). Les architectures `amd64` et `arm64` sont
  prises en charge.
- Environ **300 Mo de mémoire** disponibles et quelques centaines de Mo de disque, plus la place
  qu'occupent vos fichiers et pièces jointes.
- Le **réseau de l'hôte** (`network_mode: host`, Linux) pour le conteneur. Sans lui tout fonctionne,
  sauf que votre téléphone ne trouvera pas le hub tout seul : vous taperez son adresse.
- L'**adresse de la machine sur votre réseau domestique**, par exemple `192.168.1.20`. La liste des
  appareils connectés de votre box l'indique. Idéalement, demandez à la box de toujours donner la
  même adresse à cette machine.

---

## 3. Installation

### 3.1 Créer un dossier et deux fichiers

Créez un dossier pour SyncHub sur la machine (par exemple `/volume1/docker/synchub` ou
`~/synchub`) et placez-y ces deux fichiers.

**`compose.yml`**

```yaml
name: synchub

services:
  synchub:
    image: ghcr.io/mambocoding/synchub:${SYNCHUB_TAG:?set SYNCHUB_TAG in the .env beside this file}
    restart: unless-stopped
    network_mode: host
    cap_drop: [ALL]
    security_opt:
      - no-new-privileges:true
    read_only: true
    tmpfs:
      - /tmp
    volumes:
      - synchub-data:/data
      - launcher-state:/launcher
    environment:
      SYNCHUB_BIND: "0.0.0.0"
      # L'adresse de votre machine sur le réseau domestique, après synchub.local. Obligatoire.
      SYNCHUB_ALLOWED_HOSTS: "synchub.local,192.168.XXX.XXX"
      SYNCHUB_TLS_KEYSTORE_PASSWORD: "${SYNCHUB_TLS_KEYSTORE_PASSWORD:?set it in the .env beside this file}"
      # Votre fuseau horaire, pour que les dates des pages web soient justes.
      TZ: "Europe/Paris"
      # Facultatif, nécessaire pour la double authentification (section 9).
      # SYNCHUB_SECRET_KEY: ""

  # Facultatif : le lanceur, qui ajoute un bouton « Appliquer la mise à jour » (section 10.2).
  synchub-launcher:
    profiles: ["launcher"]
    image: ghcr.io/mambocoding/synchub-launcher:${SYNCHUB_LAUNCHER_TAG:-latest}
    restart: unless-stopped
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro
      - launcher-state:/state
      - ${SYNCHUB_PROJECT_DIR:-/unset}:${SYNCHUB_PROJECT_DIR:-/unset}
      - ${SYNCHUB_PROJECT_DIR:-/unset}/compose.yml:${SYNCHUB_PROJECT_DIR:-/unset}/compose.yml:ro
    environment:
      SYNCHUB_PROJECT_DIR: "${SYNCHUB_PROJECT_DIR:-}"
      SYNCHUB_COMPOSE_PROJECT: "${SYNCHUB_COMPOSE_PROJECT:-synchub}"
      SYNCHUB_SERVICE: "synchub"
      SYNCHUB_LAUNCHER_POLL_SECONDS: "${SYNCHUB_LAUNCHER_POLL_SECONDS:-10}"

volumes:
  synchub-data:
    name: synchub-data
  launcher-state:
    name: synchub-launcher-state
```

**`.env`** (le nom commence par un point)

```sh
# La version de SyncHub à faire tourner : trois nombres, jamais « latest ».
SYNCHUB_TAG=

# Un mot de passe qui protège le certificat du hub. Choisissez-le maintenant et ne le changez jamais.
SYNCHUB_TLS_KEYSTORE_PASSWORD=

# Uniquement pour le lanceur facultatif (section 10.2) : le chemin absolu de ce dossier.
SYNCHUB_LAUNCHER_TAG=latest
SYNCHUB_PROJECT_DIR=
```

### 3.2 Renseigner quatre valeurs

| Où | Quoi écrire |
| --- | --- |
| `.env` → `SYNCHUB_TAG` | La version actuelle. Elle est publiée sur <https://raw.githubusercontent.com/Mambocoding/io/main/synchub/latest.json> (champ `version`), par exemple `0.2.216`. |
| `.env` → `SYNCHUB_TLS_KEYSTORE_PASSWORD` | Un long mot de passe aléatoire. Gardez-en une copie : s'il est perdu, le hub ne peut plus ouvrir son certificat et chaque téléphone doit être associé à nouveau. |
| `compose.yml` → `SYNCHUB_ALLOWED_HOSTS` | Remplacez `192.168.XXX.XXX` par l'adresse de votre machine. Le hub refuse toute requête vers une adresse absente de cette liste, avec un simple *Bad Request*. |
| `compose.yml` → `TZ` | Votre fuseau horaire (`Europe/Paris`, `Europe/Brussels`, `Europe/Zurich`, `America/Montreal`…). |

Gardez `compose.yml` et `.env` **ensemble** dans le même dossier : le premier ne démarre pas sans le
second.

### 3.3 Démarrer

Dans ce dossier :

```sh
docker compose up -d
docker compose logs synchub
```

Aucun compte ni mot de passe n'est nécessaire pour télécharger l'image. Beaucoup de gestionnaires
de conteneurs de NAS savent aussi importer un `compose.yml` comme « projet » : le résultat est le
même.

Dans le journal, cherchez ces lignes :

```
First run: admin account created.
Setup token (use as the admin password): ...
Serving https://192.168.1.20:8443
TLS certificate SHA-256 fingerprint: A1:B2:...
```

Copiez le **jeton de configuration** (*setup token*) : c'est le premier mot de passe du compte
administrateur.

---

## 4. Première connexion

1. Dans un navigateur sur votre réseau domestique, ouvrez **`https://synchub.local:8443`** ou
   **`https://<adresse de votre machine>:8443`**.
2. Le navigateur prévient que la connexion n'est pas fiable. C'est normal la première fois :
   acceptez l'avertissement pour continuer. La [section 6](#6-un-cadenas-dans-le-navigateur) le
   supprime définitivement.
3. Connectez-vous avec l'utilisateur `admin` et le jeton de configuration comme mot de passe.
4. Un **assistant de configuration** s'ouvre : il vous guide pour associer un téléphone, activer la
   double authentification, choisir l'adresse qu'utiliseront vos téléphones et régler le réseau.
   Vous pouvez y revenir à tout moment depuis **Paramètres → Configuration**.
5. Changez le mot de passe administrateur : **Paramètres → Compte → Changer le mot de passe**
   (12 caractères minimum).

**Activez les applications que vous utilisez** dans **Paramètres → Applications** (administrateur
uniquement). Chacune s'active ou se désactive immédiatement, sans redémarrage.

---

## 5. Associer un téléphone

1. Dans l'application sur votre téléphone, ouvrez les réglages du hub. L'application **trouve le hub
   toute seule** sur votre réseau et propose *SyncHub à 192.168.1.20*. Sinon, tapez
   `https://<adresse>:8443`.
2. Dans le navigateur, ouvrez **Paramètres → Appareils → Associer un appareil**. Un **QR code**
   s'affiche, avec en dessous un code, l'adresse et l'empreinte du certificat.
3. **Scannez le QR code** avec l'application. Préférez le scan à la saisie : l'application vérifie
   alors l'empreinte du certificat exactement, caractère par caractère.
4. Le code est valable **cinq minutes** et **une seule fois**. S'il expire, appuyez de nouveau sur
   *Associer un appareil*.

Le téléphone appartient au compte qui a créé le code. Chaque application (flux, météo, bourse,
notes) s'associe séparément et apparaît sur sa propre ligne dans **Paramètres → Appareils**.

**Lisez la colonne *Synchronisé***, pas *Vu pour la dernière fois* : *Vu pour la dernière fois* dit
seulement que le téléphone a frappé à la porte ; *Synchronisé* dit que des données ont vraiment
transité. *jamais* signifie que la première vraie synchronisation du téléphone n'a pas encore eu
lieu.

---

## 6. Un cadenas dans le navigateur

Le certificat du hub est fabriqué par le hub lui-même : aucun navigateur ne lui fait confiance
d'emblée. Votre téléphone n'est pas concerné (il retient le certificat exact lors de l'association),
mais le navigateur vous avertit à chaque fois. Pour supprimer l'avertissement, installez **une fois**
le **certificat racine** du hub sur chaque ordinateur ou téléphone depuis lequel vous naviguez.

### 6.1 Le télécharger

En tant qu'administrateur, ouvrez **Paramètres → Appareils**, rubrique **Confiance du navigateur**,
et appuyez sur **Télécharger le certificat racine**. Vous obtenez un fichier `synchub-ca.crt`.

Cette racine ne peut garantir que `synchub.local`, `localhost` et les adresses de votre hub — rien
d'autre sur Internet.

> **Pas de bouton de téléchargement ?** La rubrique n'est visible **que des administrateurs**. Si
> vous êtes administrateur et que la rubrique indique que le hub ne détient pas de certificat racine,
> votre hub a été installé avant cette fonction : il conserve son ancien certificat et ne le
> remplacera jamais de lui-même. Le seul moyen d'obtenir une racine est de supprimer le certificat
> (`/data/keystore.p12`) puis de redémarrer, ce qui **oblige chaque téléphone associé à confirmer le
> nouveau certificat** (Paramètres → Appareils affiche un QR code pour cela) ou à être associé de
> nouveau. D'ici là, continuez d'accepter l'avertissement du navigateur.

### 6.2 L'installer

**Windows** (Edge, Chrome)
1. Double-cliquez sur `synchub-ca.crt` → **Installer le certificat…**
2. Choisissez **Utilisateur actuel** → **Suivant**.
3. Choisissez **Placer tous les certificats dans le magasin suivant** → **Parcourir…** →
   **Autorités de certification racines de confiance** → **OK** → **Suivant** → **Terminer**.
4. Confirmez l'avertissement de sécurité par **Oui**, puis fermez et rouvrez le navigateur.

**macOS** (Safari, Chrome)
1. Double-cliquez sur `synchub-ca.crt` : le Trousseau d'accès s'ouvre et l'ajoute au trousseau
   *session*.
2. Double-cliquez sur le certificat *SyncHub Local CA* → **Se fier** → *Lors de l'utilisation de ce
   certificat* : **Toujours approuver**. Fermez la fenêtre et saisissez votre mot de passe.

**Android**
1. Ouvrez les **Paramètres** du téléphone → **Sécurité et confidentialité** → **Plus de paramètres
   de sécurité** → **Chiffrement et identifiants** → **Installer un certificat** → **Certificat CA**.
2. Confirmez l'avertissement et choisissez `synchub-ca.crt` dans vos téléchargements.
3. Les noms de menus varient un peu selon les fabricants : cherchez « certificat » dans les
   paramètres.

**Linux** (Chrome, Chromium) — **Paramètres → Confidentialité et sécurité → Sécurité → Gérer les
certificats**, importez le fichier comme **autorité** de confiance.

**Firefox** (tous systèmes) a sa propre liste — **Paramètres → Vie privée et sécurité → Certificats
→ Afficher les certificats… → Autorités → Importer…**, puis cochez **Confirmer cette AC pour
identifier des sites web**.

Rouvrez ensuite `https://synchub.local:8443` : le cadenas est là.

---

## 7. Plusieurs personnes, un seul hub

- **Chaque compte a tout en propre** : flux, marques de lecture, villes, liste de valeurs, notes,
  réglages. Rien n'est partagé entre comptes, et aucun réglage ne le permet.
- Un compte tout neuf est donc **vide** — ce n'est pas une perte de données.
- Un administrateur crée et supprime des comptes et peut définir un nouveau mot de passe pour
  quelqu'un qui a oublié le sien (**Paramètres → Utilisateurs**), mais **ne peut jamais lire** les
  données d'une autre personne.
- Rôles : chaque compte est *utilisateur* ; **admin** gère le hub ; **updater** peut seulement
  appliquer les mises à jour.

---

## 8. Vos fichiers

Chaque compte a un **espace de fichiers** privé, accessible depuis n'importe quel client WebDAV (le
gestionnaire de fichiers de votre ordinateur le parle généralement). Créez un jeton dans
**Paramètres → Compte**, puis connectez votre client à `https://<hub>:8443/files/` avec votre nom de
compte et ce jeton — jamais votre mot de passe.

---

## 9. Double authentification

La double authentification ajoute à votre mot de passe un code à six chiffres fourni par une
application d'authentification. Elle est facultative sur un hub qui reste à la maison, et
**fortement conseillée** si vous accédez au hub depuis l'extérieur.

**Avant que le premier compte ne l'active**, le hub a besoin d'une clé secrète :

1. Générez-en une : `openssl rand -base64 32`.
2. Placez-la dans `compose.yml` → `SYNCHUB_SECRET_KEY: "<la clé>"` (retirez le `#`), puis
   `docker compose up -d`.
3. **Gardez une copie de cette clé en lieu sûr et ne la changez jamais.** Si elle est perdue, chaque
   compte qui utilise la double authentification doit être réinitialisé par un administrateur, et
   la restauration d'une sauvegarde exige la même clé.

Ensuite, chaque personne : **Paramètres → Compte**, scanne le QR code avec une application
d'authentification, confirme avec un code, et **conserve les dix codes de récupération** affichés
une seule fois.

Tant que la clé n'est pas définie, le journal indique `SYNCHUB_SECRET_KEY is not set: two-factor
enrolment is refused until it is.` — sans conséquence si vous ne l'utilisez pas.

---

## 10. Mettre à jour

Le hub vérifie une fois par jour si une nouvelle version existe et l'indique à l'administrateur dans
**Paramètres → À propos**, avec ce que la nouvelle version vous demande (en général, rien).

### 10.1 À la main — trois étapes

1. Dans `.env`, mettez `SYNCHUB_TAG` à la nouvelle version.
2. `docker compose pull`
3. `docker compose up -d`

Sans l'étape 1, le téléchargement récupère la version que vous avez déjà.

### 10.2 Avec un bouton — le lanceur (facultatif)

Le lanceur est un second petit conteneur qui applique une mise à jour quand un administrateur appuie
sur **Appliquer la mise à jour** dans **Paramètres → À propos**, et qui note chaque arrêt du hub et
sa cause.

1. Dans `.env`, mettez `SYNCHUB_PROJECT_DIR` au chemin absolu de votre dossier SyncHub.
2. `docker compose --profile launcher up -d`

**Sachez ce que vous autorisez** : le lanceur détient la prise du moteur de conteneurs, ce qui
revient au contrôle total de la machine. Il ne reçoit du hub aucune autre instruction que « vas-y »
et n'installe jamais qu'une version officielle de SyncHub. Si c'est trop pour vous, mettez à jour à
la main.

---

## 11. Sauvegardes

- **Chaque jour à 3 h 30**, le hub enregistre un instantané de sa **configuration** (comptes,
  appareils associés, jetons, réglages). **Paramètres → Sauvegarde** les liste, en prend un à la
  demande (**Prendre un instantané maintenant**), les télécharge, les importe et les restaure
  (**Restaurer…**).
- Vos **données** (articles, notes, listes de valeurs…) ne sont pas dans un instantané : elles
  vivent aussi sur vos téléphones et en reviennent.
- Par défaut, les instantanés sont sur le même disque que les données. Copiez-les ailleurs avec
  l'outil de sauvegarde de votre NAS — **pointez-le sur le dossier des instantanés**, pas sur la base
  de données en service, qui ne peut pas être copiée sans risque pendant que le hub tourne.
- Les applications peuvent aussi déposer leurs propres sauvegardes sur le hub :
  **Paramètres → Sauvegardes** liste les vôtres.

Restaurer sur une nouvelle machine : installez le hub, utilisez **la même `SYNCHUB_SECRET_KEY`**, et
choisissez *Restaurer un instantané* à la première étape de configuration. Chaque téléphone confirme
ensuite une fois le nouveau certificat.

---

## 12. Y accéder hors de chez soi

SyncHub n'ouvre jamais de lui-même de porte vers Internet. Pour l'atteindre hors de chez vous,
utilisez un **VPN** vers votre réseau domestique — c'est le moyen le plus simple et le plus sûr. Si
vous utilisez plutôt un proxy inverse :

- ajoutez à `SYNCHUB_ALLOWED_HOSTS` l'adresse qu'utilise votre téléphone ;
- activez d'abord la **double authentification** pour chaque compte.

---

## 13. Lire le journal de démarrage

`docker compose logs synchub` montre ce que le hub a fait au démarrage. Le journal est en anglais.
Ce que signifient les lignes habituelles :

| Ligne | Signification | Que faire |
| --- | --- | --- |
| `SLF4J(W): No SLF4J providers were found` et `WARNING: A restricted method… sqlite-jdbc` | Messages de bibliothèques internes au hub. | Rien. |
| `Applied migration V…` | La base de données a été mise à niveau pour la nouvelle version. | Rien. |
| `First run: admin account created.` + `Setup token…` | Le hub a démarré sur un volume de données **vide**. | À la toute première installation : connectez-vous avec le jeton. **Après une mise à jour : votre volume de données n'a pas été conservé** — voir la [section 14](#14-en-cas-de-problème). |
| `SYNCHUB_SECRET_KEY is not set…` | La double authentification n'est pas disponible. | Rien, ou la [section 9](#9-double-authentification). |
| `Data directory: /data — docker volume "synchub-data"` | L'endroit où vivent vos données. | Vérifiez qu'il nomme le **même** volume après chaque mise à jour. |
| `Allowed Host headers: [synchub.local, 192.168.1.20]` | Les adresses auxquelles le hub répond. | L'adresse utilisée par votre téléphone et votre navigateur doit y figurer. |
| `TLS: adopted the existing keystore…` | Le hub a conservé son certificat. Normal à chaque démarrage après le premier. | Rien. |
| `TLS keystore … is readable by group or others` | Le fichier qui contient la clé privée du certificat est lisible par d'autres sur la machine. | Une fois : `docker compose exec synchub chmod 600 /data/keystore.p12`, puis redémarrez. Rien d'autre ne change. |
| `Serving https://192.168.1.20:8443` | L'adresse à ouvrir. Elle est aussi annoncée sur votre réseau, pour que les téléphones la trouvent. | Rien. Si vous voyez *not advertising*, la même ligne dit pourquoi. |
| `TLS handshake refused by 192.168.1.42 — the peer rejected this hub's certificate` | L'appareil à cette adresse a refusé le certificat du hub. | Si c'est un **ordinateur** : son navigateur ne fait pas encore confiance au hub, voir la [section 6](#6-un-cadenas-dans-le-navigateur). Si c'est un **téléphone associé** : son certificat est périmé, scannez le QR code de **Paramètres → Appareils**. |
| `RSS: N subscription(s) … scraped on the phone — not fetched here` | Des flux que votre téléphone lit lui-même et que le hub laisse de côté. | Rien. |
| `Stocks: N instrument(s) … with no symbol any role speaks` | Le hub ne peut pas récupérer le cours de ces valeurs. | Vérifiez les adresses de la page de réglages de la bourse ; si cela persiste, signalez-le. |
| `sync: …` | Une ligne par synchronisation avec un téléphone. | Utile pour voir si un téléphone synchronise vraiment. |

---

## 14. En cas de problème

**Le navigateur n'affiche que *Bad Request*.** L'adresse saisie n'est pas dans
`SYNCHUB_ALLOWED_HOSTS`. Ajoutez-la dans `compose.yml`, puis `docker compose up -d`. Une fois que le
hub a enregistré cette valeur, modifiez-la plutôt depuis **Paramètres → Configuration**.

**Après une mise à jour, le journal affiche un nouveau jeton de configuration et chaque téléphone
demande à être associé de nouveau.** Le hub a démarré sur un volume de données **vide** : vos
données n'ont pas été effacées, elles sont dans un autre volume. Lancez `docker volume ls` et
vérifiez que `/data` pointe sur `synchub-data`. Dans le formulaire de conteneur de votre NAS, la
ligne du volume ne doit jamais rester vide.

**Ne lancez jamais `docker compose down -v`** (ni `docker volume prune`) : `-v` **supprime** le
volume de données — base, certificat et toutes les associations. `docker compose up -d`, `restart`
et `down` sans `-v` sont sans danger.

**Le téléphone dit que le certificat du hub a changé depuis l'association.** Le hub a un nouveau
certificat. Ouvrez **Paramètres → Appareils** et scannez avec l'application le QR code qui s'y
trouve : le téléphone garde son association et fait confiance au nouveau certificat. Si le hub a
aussi perdu ses données, associez plutôt à nouveau avec **Associer un appareil**.

**Le téléphone dit que le hub est injoignable.** Vérifiez dans l'ordre : le hub tourne ; le
téléphone est sur le réseau domestique ; l'adresse qu'il utilise figure dans
`SYNCHUB_ALLOWED_HOSTS` (ligne `Allowed Host headers` du journal) ; ouvrez la même adresse
`https://…` dans le navigateur du téléphone.

**Un appareil est vert dans Paramètres → Appareils mais rien ne s'affiche.** Regardez
*Synchronisé* : *jamais* signifie qu'aucune donnée n'a encore transité. **Paramètres →
Synchronisation** montre, collection par collection, ce que le hub détient pour votre compte.

**`https://synchub.local:8443` ne s'ouvre pas sur un téléphone Android.** Les navigateurs Android ne
résolvent pas les noms en `.local`. Utilisez l'adresse (`https://192.168.1.20:8443`). L'application
n'est pas concernée : elle trouve le hub autrement.

---

*Questions : ouvrez une « issue » dans ce dépôt. Politiques de confidentialité des applications :
[`privacy/`](../../privacy/).*
