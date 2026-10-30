# UCE Tool

[简体中文](README.zh-CN.md) | [English](README.en.md) | [Deutsch](README.de.md) | [日本語](README.ja.md) | **Français**

UCE Tool est l'application de bureau du USB-C Explorer. Elle affiche les mesures en direct, lit les données E-Marker, détecte les protocoles de charge, met à jour le micrologiciel et configure les couleurs de l'appareil.

Elle prend en charge Windows 64 bits et les Mac Apple Silicon ou Intel, avec une interface en chinois, anglais, allemand, japonais et français.

**[Télécharger la dernière version](https://github.com/Tamako-zz/UCE-Tool/releases/latest)** · **[Toutes les versions](https://github.com/Tamako-zz/UCE-Tool/releases)**

## Sommaire

- [Téléchargement et installation](#download)
- [Connexion de l'appareil](#connect)
- [Tableau de bord et graphique](#dashboard)
- [E-Marker et historique](#emarker)
- [Protocoles de charge et PDO](#protocol)
- [Mise à jour du micrologiciel](#firmware)
- [Couleurs de l'appareil](#theme)
- [Langue, apparence et informations](#settings)
- [Mise à jour de UCE Tool](#software-update)
- [Dépannage](#faq)

<a id="download"></a>
## Téléchargement et installation

Sur la [page des versions](https://github.com/Tamako-zz/UCE-Tool/releases/latest), ouvrez **Assets** et choisissez le fichier adapté :

| Fichier | Plateforme | Application |
| --- | --- | --- |
| `UCE-Windows-x64.zip` | Windows 64 bits, Intel / AMD | `UCE.exe` |
| `UCE-mac-arm64.dmg` | Mac Apple Silicon (série M) | `UCE.app` |
| `UCE-mac-x86_64.dmg` | Mac Intel | `UCE.app` |

Sur Mac, le processeur est indiqué dans **menu Apple → À propos de ce Mac**.

**Windows :** extrayez complètement le ZIP, puis ouvrez `UCE.exe` depuis le dossier extrait.

**macOS :** ouvrez le DMG adapté, glissez `UCE.app` vers **Applications**, éjectez l'image disque, puis ouvrez UCE depuis Applications. Si macOS bloque le premier lancement, vérifiez la provenance et autorisez l'ouverture dans **Réglages Système → Confidentialité et sécurité**.

<a id="connect"></a>
## Connexion de l'appareil

Il vous faut un USB-C Explorer, un câble USB permettant le transfert de données et un micrologiciel APP adapté au matériel. Les fonctions de thème et de détection nécessitent aussi un micrologiciel compatible.

1. Lancez UCE Tool et connectez l'appareil à l'ordinateur par son interface de données.
2. Le logiciel recherche les appareils et tente de se connecter automatiquement. Vérifiez l'état **Connecté** à gauche.
3. Ouvrez la page souhaitée. La carte affiche le nom, une partie du numéro de série et la version APP ; le numéro complet figure dans les paramètres.

Cliquez sur une carte pour changer d'appareil. Attendez la fin d'une mise à jour avant de changer. Le **mode BOOT** permet de restaurer l'APP par mise à jour du micrologiciel ; les mesures en direct nécessitent une APP fonctionnelle.

<a id="dashboard"></a>
## Tableau de bord et graphique

Connectez l'appareil, ouvrez le **Tableau de bord** et cliquez sur l'icône de démarrage. Les valeurs et le graphique se mettent à jour à la réception des mesures.

| Canal | Signification |
| --- | --- |
| VBUS / IBUS / POWER | Tension (V), courant (A) et puissance (W) |
| D+ / D− | Tensions des lignes de données USB |
| CC1 / CC2 | Tensions des broches CC USB-C |

Cliquez sur les canaux pour afficher ou masquer leurs courbes. La tension, le courant et la puissance ont des échelles distinctes. Survolez le graphique pour consulter les mesures ; `--` indique l'absence de donnée à cet endroit.

Fréquences d'échantillonnage : **1, 10 ou 50 SPS** ; fenêtre d'affichage : **10, 30, 60 ou 120 secondes**. Le bouton d'arrêt met l'acquisition en pause ; la durée de pause n'est pas comptée à la reprise. Effacer supprime l'historique et remet le temps à zéro. Après un effacement en pause, redémarrez l'acquisition.

<a id="emarker"></a>
## E-Marker et historique

Connectez le câble au port indiqué, ouvrez **E-Marker** et cliquez sur **Lire** ou **Lecture continue**. Avant la détection continue, débranchez tous les autres appareils alimentés de la sortie. Le même bouton arrête la lecture continue.

Selon les données fournies, la page affiche le type de câble, le courant nominal, la tension maximale, la vitesse USB, la version PD, TBT, EPR et la longueur ou latence. Les champs non communiqués ou non reconnus indiquent « Inconnu ». Si aucun E-Marker n'est détecté, vérifiez le câble et son branchement. Les VDO bruts figurent sous l'illustration.

Les lectures réussies sont ajoutées à l'historique de la session. L'export crée un fichier `.xlsx` avec la date, les informations du câble et les VDO bruts. Les dates utilisent UTC+8. L'historique est effacé à la fermeture : exportez les données à conserver.

<a id="protocol"></a>
## Protocoles de charge et PDO

Connectez le chargeur ou la source au port indiqué, ouvrez **Détection PD** et lancez la détection. La tension peut augmenter pendant le test : débranchez d'abord les appareils alimentés de la sortie. Le même bouton permet d'arrêter la détection.

La page présente la tension, le courant et la puissance des PDO ainsi que l'état de chaque test : réussi, échoué, en attente ou non pris en charge. Les tests disponibles dépendent du micrologiciel de l'appareil. Si l'appareil est occupé, arrêtez le test en cours avant une autre opération.

<a id="firmware"></a>
## Mise à jour du micrologiciel

Cette page met à jour le micrologiciel **de l'USB-C Explorer**.

1. Connectez l'appareil et ouvrez **Mise à jour du micrologiciel**.
2. Cliquez sur **Obtenir les versions** pour charger la liste.
3. Consultez les notes et choisissez une version compatible avec votre matériel. Si plusieurs fichiers BIN sont proposés, choisissez le bon selon les notes.
4. Cliquez sur **Mettre à jour** dans la carte correspondante. Le fichier choisi est téléchargé, vérifié, puis transmis à l'appareil. La carte affiche la progression et le résultat.

Seul le fichier sélectionné est téléchargé ; le fichier temporaire est nettoyé après l'opération. Gardez l'USB connecté et ne changez pas d'appareil pendant la mise à jour. Ensuite, actualisez les informations dans les paramètres pour vérifier la version APP. En cas d'échec, conservez le message, vérifiez la connexion et la compatibilité, puis réessayez.

<a id="theme"></a>
## Couleurs de l'appareil

Ouvrez **Configuration du thème**, utilisez les flèches pour changer de page d'aperçu, cliquez sur les zones modifiables et choisissez la couleur d'arrière-plan sous l'aperçu. **Appliquer à l'appareil** permet de prévisualiser les couleurs ; **Enregistrer sur l'appareil** les conserve après redémarrage.

L'aperçu comprend les mesures, statistiques, E-Marker, protocoles et paramètres. Dans les statistiques, les zones configurables comprennent le titre, MAX, CUR, Ah et Wh. Leur modification nécessite un micrologiciel compatible.

| Action | Effet |
| --- | --- |
| Rétablir les valeurs par défaut | Réinitialiser les couleurs de l'aperçu |
| Lire depuis l'appareil | Remplacer l'aperçu par les couleurs actuelles |
| Appliquer à l'appareil | Prévisualiser sans enregistrer durablement |
| Enregistrer sur l'appareil | Appliquer et conserver après redémarrage |

Survolez les boutons pour afficher leur description. Si une zone ne change pas sur l'appareil, vérifiez la prise en charge par son micrologiciel.

<a id="settings"></a>
## Langue, apparence et informations

Dans **Langue de l'interface**, choisissez 简体中文, English, Deutsch, 日本語 ou Français. Le choix est enregistré et ne change pas la langue de l'appareil. Les notes de version utilisent les traductions fournies par leur auteur ; les données brutes restent inchangées.

Les commandes de la barre latérale permettent de changer le thème clair/sombre et de masquer ou afficher la navigation. L'apparence du logiciel et les couleurs de l'appareil sont indépendantes. Les paramètres affichent le modèle, le micrologiciel, le numéro de série complet et le lot ; actualisez pour les relire. Consultez le journal d'activité en cas de problème.

<a id="software-update"></a>
## Mise à jour de UCE Tool

Cette fonction met à jour **l'application de bureau**, pas le micrologiciel de l'appareil. Sous Windows, utilisez le menu **À propos → Rechercher des mises à jour** en haut de la fenêtre ; sous macOS, utilisez **UCE → Rechercher des mises à jour** dans le menu système.

Suivez les instructions si un paquet compatible est disponible. Sinon, téléchargez le paquet adapté sur la page des versions et remplacez l'ancienne application après l'avoir fermée. Terminez d'abord toute opération sur le micrologiciel. Les anciennes versions Mac sans prise en charge des mises à jour DMG nécessitent une installation manuelle initiale de la nouvelle version.

<a id="faq"></a>
## Dépannage

- **Appareil non connecté :** vérifiez le câble de données et le port USB, fermez les autres outils série et vérifiez que l'APP est compatible. Si le système reconnaît l'appareil mais pas UCE Tool, consultez le journal.
- **Pas de mesures ou de courbe :** vérifiez la connexion et démarrez l'acquisition. Les mesures ne continuent pas en pause ou en mode BOOT.
- **Champ E-Marker inconnu :** le câble ou le micrologiciel peut ne pas fournir cette information. Consultez les VDO bruts et les autres résultats.
- **Requête GitHub échouée ou limitée :** vérifiez le réseau et le proxy, réessayez plus tard ou sur un autre réseau, et conservez le message complet. En cas d'erreur de certificat avec une ancienne version Mac, installez une version plus récente contenant le correctif.
- **Couleurs non appliquées :** connectez l'appareil et appliquez ou enregistrez les couleurs ; vérifiez la compatibilité du micrologiciel. Pour conserver les couleurs après redémarrage, utilisez Enregistrer.
- **Quel fichier Mac ?** `arm64` pour Apple Silicon, `x86_64` pour Intel. Consultez « À propos de ce Mac ».
- **Mise à jour automatique indisponible :** téléchargez le paquet adapté depuis la page des versions et remplacez manuellement l'ancienne application après l'avoir fermée.

Pour signaler un problème, indiquez le système et le processeur, la version de UCE Tool, les versions matérielle et APP de l'appareil, les étapes, le message d'erreur complet ou une capture, ainsi que les journaux utiles.
