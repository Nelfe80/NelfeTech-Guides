# Gestionnaire de salle

Le Fleet Hub supervise vos bornes RetroBat, identifie les joueurs, anime tournois et écrans. **Offline-first** : le hub écoute les bornes, il ne les commande pas — sans réseau ni hub, chaque borne continue de fonctionner, et la licence n'éteint jamais une borne.

## Installer

1. **Achetez la licence** adaptée sur [nelfetech.com/salles](https://nelfetech.com/salles.html) — la licence se compte **par borne équipée**, hub inclus.
2. **Installez le hub** sur une machine du réseau local de la salle (le PC du comptoir convient très bien) : dézippez la release — comme APIExpose, tout tient dans **un seul exécutable à la racine**, `RetroBat.Hub.exe`, avec son dossier `wwwroot` à côté.
3. **Double-cliquez `RetroBat.Hub.exe`**, puis ouvrez **http://localhost:12400** dans un navigateur : c'est la console de la salle (Ma salle, Joueurs, tournois, leaderboard, Paramètres). Toute la configuration et l'état de la salle vivent à côté de l'exe (`appsettings.json`, dossier `state\` — sauvegardez ce dossier, il contient vos scores, votre licence et vos clés). L'installeur Windows optionnel ajoute le démarrage automatique avec la session.
4. **Activez la clé** dans Paramètres (première saisie = activation ; fonctionne ensuite 14 jours sans internet).
5. **Enrôlez vos bornes** : bouton « 🔍 Rechercher des bornes » dans Paramètres (le hub scanne le réseau local), ou saisie de l'adresse `http://IP-de-la-borne:12345`. Redémarrez le hub pour les connecter.

Dans **Ma salle**, le crayon ✏️ à côté du nom d'une borne la **renomme** (« Bartop bar », « Cockpit »…) — le nom est immédiat et conservé. Le bouton **Quitter le jeu** ferme proprement le jeu en cours, qu'il tourne sous RetroArch **ou** un émulateur autonome (MAME, PCSX2…).

## Identification des joueurs

- **QR de borne** : activez `CabinetBadgeOverlay` dans la configuration APIExpose de la borne — le QR d'identification et le numéro s'affichent en bas à droite de l'écran, et disparaissent pendant qu'un joueur est connecté. Une planche de **stickers** imprimables existe aussi.
- Le joueur **scanne le QR de la borne avec son téléphone** (ou tape le numéro de la borne) et entre son code joueur. Re-scan = départ.
- Créez les badges au comptoir via la page joueurs — identités anonymes, aucune donnée personnelle.

## Écrans de la salle

Sur chaque affichage physique, ouvrez `screen.html?name=ecran-bar` (un nom par écran). Depuis la console, vous choisissez ce que **chaque** écran montre : leaderboard, écran tournoi, mosaïque de flotte… Un écran **garde son contenu** — podium compris — tant que vous ne le changez pas.

!!! tip "Annoncer un joueur"
    Routez un écran vers la **carte publique** d'un joueur (`…/retrocreator/card/SonPseudo`) : avatar, palmarès et top 3 s'affichent en grand — parfait pour présenter un champion ou inviter un joueur à rejoindre une borne.

## Mon flux screen — écrans, régie vidéo et stream

L'onglet **Mon flux screen** de la console pilote tout l'affichage et le direct de la salle.

**Appairer un écran.** Sur une smart TV ou un mini-PC, ouvrez `http://<hub>:12400/screen.html` : l'écran affiche un **code à 6 chiffres**. Saisissez-le dans l'onglet, nommez l'écran (« TV entrée ») — c'est mémorisé, même après un redémarrage de la TV. L'écran branché directement sur le PC du hub s'affiche en un clic (« Afficher ici »), sans code.

**Choisir le contenu.** Par écran : une vue fixe ou la rotation des vues — **Leaderboard live** (les rangs glissent quand un joueur en double un autre, les scores tournent comme un compteur), **Mur des records**, **Événements**, **Parties en cours**. Pour le leaderboard, choisissez : salle en continu, challenge en cours, ou automatique. La **régie manuelle** force une vue sur tous les écrans d'un coup (moment fort), puis « Reprendre le programme ».

**Les parties en direct sur les écrans.** La régie vidéo diffuse le jeu des bornes sur vos écrans en moins d'une seconde (borne choisie, rotation, ou bascule automatique en tournoi). Une borne **libre** est diffusable par défaut ; une borne **occupée** ne passe à l'écran que si le joueur l'a **autorisé dans son app** — c'est sa règle, pas la vôtre.

**Le stream de la salle.** Collez la clé de stream Twitch de la salle (conservée chiffrée), appuyez sur « Démarrer la régie » : la composition (parties, classements, habillage) part en direct sur votre chaîne. L'**habillage** est automatique et se règle en trois cases : bandeau bas au nom de la salle, logo de la salle (à charger dans Paramètres, à côté de l'adresse), cartouche par borne (joueur, jeu et son logo, événement en cours).

## Sponsoring

Déposez vos images et vidéos de pub dans le dossier `sponsors` (à côté du hub), ou ajoutez un lien YouTube / une chaîne Twitch. Chaque campagne se règle dans **Mon flux screen** : activée, dates de début/fin, fréquence de passage, durée. Quand une campagne est due, **tous les écrans la passent en même temps**, en fondu par-dessus leur contenu — de la visibilité vendable à vos partenaires.

## Classements en ligne (optionnel)

Votre salle peut rejoindre les classements publics : le hub signe chaque lot de scores (clé propre à la salle) et les pousse quand internet est là — jamais l'inverse : le jeu ne dépend de rien. L'enrôlement se fait avec la clé publique du hub (visible dans la console) ; les joueurs badgés retrouvent alors leurs marques « salle vérifiée » sur leur compte en ligne.

**Renseignez la fiche de votre salle** (ville, région, pays, enseigne) à l'enrôlement : c'est ce qui place vos joueurs dans les classements à chaque échelle — champions de la salle, de la ville, de l'enseigne, de la région, du pays et du monde.

## Rôles et modération

Sur la plateforme en ligne, une salle peut déléguer des **rôles** cloisonnés à des comptes NelfeTech :

- **propriétaire** — tous les droits sur la salle ;
- **modérateur** — peut **masquer un pseudo** inapproprié sur les classements publics (il s'affiche alors `##;-)##`) ;
- **organisateur** — **annonce des événements** aux joueurs qui suivent la salle (jamais de commande vers les bornes).

Les outils correspondants apparaissent dans l'onglet **Config** du compte concerné. (Attribution des rôles côté plateforme.)

## Tournois

Voir le [guide organisateur](organisateur.md) — et avant tout événement, la règle d'or : **vérifier les signaux du jeu, puis manche de test**.
