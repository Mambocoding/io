<!-- Source: Mambocoding/FeedScraper, specs/SPEC-055-privacy-policy.md, section *The policy, verbatim — fr*, at commit 82b5037 on dev. Copied verbatim (date filled in, contact linked, language bar added); the source is right if the two ever disagree. -->

# FeedScraper — Politique de confidentialité

*[English](../) · Français · [Deutsch](../de/) · [Español](../es/) · [Nederlands](../nl/)*

*Dernière mise à jour : 2026-11-22*

FeedScraper est un lecteur de flux qui fonctionne entièrement sur votre appareil.

**Ce qui est collecté : rien.** Il n'y a ni compte ni inscription. L'application n'envoie à personne de données
d'utilisation, de statistiques, de rapports de plantage ni d'identifiant publicitaire, et elle ne contient aucune
bibliothèque qui le ferait. Personne, pas même le développeur, ne peut voir ce que vous lisez.

**Ce qui est conservé, et où.** Vos abonnements, les articles récupérés, ceux que vous avez lus ou mis en favori, les
copies enregistrées pour une lecture hors ligne et vos réglages sont conservés uniquement sur votre appareil, dans le
stockage privé de l'application. L'application désactive aussi la sauvegarde dans le cloud du système pour ses données :
rien n'est donc copié hors de l'appareil par ce moyen non plus.

**Ce qui quitte votre appareil.** Uniquement les requêtes ci-dessous, de quatre sortes :

1. **Les flux auxquels vous êtes abonné.** L'application récupère chaque flux à l'adresse que vous lui avez donnée. Quand
   vous ouvrez un article, l'enregistrez pour le lire hors ligne ou que l'application en affiche l'image, elle récupère
   cette page ou cette image sur le site vers lequel pointe le flux. Ces requêtes vont aux éditeurs des flux que vous avez
   choisis, et chacun d'eux voit ce que montre toute requête web : l'adresse demandée et l'adresse réseau depuis laquelle
   vous l'avez faite.
2. **Un hub que vous avez appairé, si vous en avez appairé un.** La synchronisation est facultative et désactivée tant
   que vous ne la configurez pas, et le hub est une machine que vous faites fonctionner vous-même — ce projet n'exploite
   aucun serveur, de quelque sorte que ce soit. Quand vous en appairez un, l'application lui envoie vos abonnements, vos
   marques de lecture, de favori et d'enregistrement, et vos réglages, et reçoit les mêmes de vos autres appareils. Elle
   n'envoie **pas** les articles enregistrés sur l'appareil, ni son propre relevé des flux dont la récupération a échoué.
   La connexion ne se fait qu'avec la machine que vous avez appairée, identifiée par un certificat que vous avez confirmé
   lors de l'appairage. Pour vous aider à trouver votre hub, l'écran d'appairage demande aux appareils de votre réseau
   domestique si un hub s'y trouve ; cette requête ne quitte pas votre réseau domestique, et vous pouvez saisir l'adresse
   du hub à la place. Joindre le hub lui-même ne va jamais au-delà de l'adresse que vous avez appairée.
3. **Les annonces, sauf si vous les désactivez.** Environ une fois par jour, tant que l'application est ouverte, elle lit
   un fichier public d'annonces dans le dépôt public du développeur. La requête est anonyme : ni compte, ni cookie, ni
   identifiant de vous ou de votre appareil. Comme toute requête web, elle montre l'adresse réseau de votre appareil à
   l'hébergeur de ce fichier. *Recevoir les annonces*, dans la liste des annonces sous *Paramètres*, l'arrête ; rien n'est
   demandé tant que c'est désactivé.
4. **Un service d'assistant que vous avez configuré, si vous en avez configuré un.** L'assistant reste désactivé tant
   que vous ne l'activez pas, n'acceptez pas ce qu'il envoie, ne saisissez pas l'adresse d'un service et votre propre
   clé, et qu'un test n'a pas réussi. Ensuite, et seulement quand vous touchez *Résumer* ou *Traduire* sur un article,
   l'application envoie le titre et le texte de cet article, ainsi que la langue d'affichage de l'application, à
   l'adresse que vous avez saisie — rien d'autre, jamais en arrière-plan. Ce service les traite selon ses propres
   conditions et sa propre politique de confidentialité, que vous avez acceptées auprès de lui, et vous facture
   directement ; le développeur ne les reçoit jamais. Votre clé reste sur cet appareil, chiffrée, et n'est jamais
   sauvegardée ni synchronisée.

Il n'y a aucune autre destination.

Trois choses quittent l'application uniquement quand vous le demandez, et uniquement vers une application de votre
téléphone : partager un article transmet son titre et son adresse à l'application que vous choisissez dans le menu de
partage du système ; ouvrir un article dans l'onglet du navigateur intégré transmet son adresse à votre navigateur, qui
récupère ensuite la page lui-même ; et lire un article à voix haute transmet son titre et son texte au moteur de synthèse
vocale réglé sur votre téléphone, dont certains utilisent des voix en ligne, un choix fait dans les réglages de votre
téléphone, pas dans cette application. Aucune d'elles ne va au développeur.

**Les autorisations, et à quoi chacune sert.** L'accès à Internet, pour récupérer les flux. L'état du réseau, pour
savoir si vous êtes sur une connexion limitée avant de télécharger des images. L'état du Wi-Fi et le multicast Wi-Fi,
utilisés uniquement pour lister les hubs de votre réseau domestique pendant que vous en appairez un ou en cherchez un qui
a changé d'adresse ; saisir l'adresse fonctionne sans eux. L'accès au réseau local, sur Android 17 et versions
ultérieures, demandé la première fois qu'une synchronisation en a besoin, pour joindre votre propre hub sur votre réseau
domestique ; le refuser conserve tous les flux sur votre téléphone et arrête seulement la synchronisation. Les
notifications, facultatives et utilisées uniquement pour les flux pour lesquels vous avez demandé à être prévenu.
L'appareil photo, facultatif, n'est demandé qu'au moment où vous touchez *Scanner* pour appairer un hub, et n'est jamais
nécessaire — vous pouvez saisir les mêmes informations à la main. Si vous activez le verrouillage de l'application,
celle-ci demande au système de vérifier votre empreinte digitale ou le code PIN de l'appareil ; elle ne reçoit ni ne
conserve jamais l'un ou l'autre.

**Emporter vos données.** L'application peut exporter vos abonnements et vos réglages dans un fichier, à l'emplacement
de votre choix. Il n'est écrit que lorsque vous le demandez.

**Supprimer vos données.** Désinstaller l'application supprime tout ce qu'elle a conservé. Il n'existe aucune copie
ailleurs à réclamer.

**Enfants.** L'application ne s'adresse pas aux enfants, et elle ne collecte rien auprès de personne, quel que soit
l'âge.

**Modifications de cette politique.** Si le comportement de l'application change, ce texte change avec lui, dans la même
version, et la date ci-dessus change.

**Qui est responsable, et votre droit de réclamation.** Le responsable du traitement de cette application est
Mambocoding, mambocoding@gmail.com. Comme l'application ne collecte rien et n'envoie rien au développeur, celui-ci ne
détient aucune donnée personnelle vous concernant à consulter, rectifier ou effacer. Si vous estimez que vos données ont
été traitées de manière illicite, vous avez le droit d'introduire une réclamation auprès d'une autorité de contrôle de
la protection des données, en particulier dans le pays où vous résidez, où vous travaillez ou où vous pensez que la
violation a eu lieu.

**Contact.** Les questions sur cette politique peuvent être posées sur le [suivi des problèmes public](https://github.com/Mambocoding/io/issues) du dépôt public du
développeur, `Mambocoding/io`, dont le lien figure sur la page de l'application dans la boutique.
