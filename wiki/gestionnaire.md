# Gestionnaire de salle

Le Fleet Hub supervise vos bornes RetroBat, identifie les joueurs, anime tournois et écrans. **Offline-first** : le hub écoute les bornes, il ne les commande pas — sans réseau ni hub, chaque borne continue de fonctionner, et la licence n'éteint jamais une borne.

## Installer

1. **Achetez la licence** adaptée sur [nelfetech.com/salles](https://nelfetech.com/salles.html) — la licence se compte **par borne équipée**, hub inclus.
2. **Installez le hub** : un exécutable unique sur une machine du réseau local de la salle.
3. **Activez la clé** dans la console d'administration (première saisie = activation ; fonctionne ensuite 14 jours sans internet).
4. **Enrôlez vos bornes** : chaque borne RetroBat+APIExpose s'ajoute par son adresse locale depuis la console.

## Identification des joueurs

- **QR de borne** : activez `CabinetBadgeOverlay` dans la configuration APIExpose de la borne — le QR d'identification et le numéro s'affichent en bas à droite de l'écran, et disparaissent pendant qu'un joueur est connecté. Une planche de **stickers** imprimables existe aussi.
- Le joueur **scanne le QR de la borne avec son téléphone** (ou tape le numéro de la borne) et entre son code joueur. Re-scan = départ.
- Créez les badges au comptoir via la page joueurs — identités anonymes, aucune donnée personnelle.

## Écrans de la salle

Sur chaque affichage physique, ouvrez `screen.html?name=ecran-bar` (un nom par écran). Depuis la console, vous choisissez ce que **chaque** écran montre : leaderboard, écran tournoi, mosaïque de flotte… Un écran **garde son contenu** — podium compris — tant que vous ne le changez pas.

## Classements en ligne (optionnel)

Votre salle peut rejoindre les classements publics : le hub signe chaque lot de scores (clé propre à la salle) et les pousse quand internet est là — jamais l'inverse : le jeu ne dépend de rien. L'enrôlement se fait avec la clé publique du hub (visible dans la console) ; les joueurs badgés retrouvent alors leurs marques « salle vérifiée » sur leur compte en ligne.

## Tournois

Voir le [guide organisateur](organisateur.md) — et avant tout événement, la règle d'or : **vérifier les signaux du jeu, puis manche de test**.
