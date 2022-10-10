# Objectif 


Bienvenue a toi cher Padawan! Ton objectif sera de créer une solution d'automatisation de serveur web à la demande pour les professionels de laconnecteam.

Ce service sera disponnible à travers un portail à la cible mais dns un premier temps pour l'administrateur (moi). Ce service va me permettre de gagner 1 journéee de travail à chaque création de site. Et vraiment c'est pas du luxe.

## Livrable

### Poussez votre mémoire
Votre mémoire se fera sous le nom memoire_yacine.md
Décrivez vos actions.

### Poussez votre code sur GIT
- Vous devez poussez sur votre BRANCHE portant votre prénom le script fonctionnel.
- Positionnez vous sur la branche:
    git checkout -t origin/loan
- Faites un add et un commit a chaque modification radicale que vous faites sur votre code:
Pour pousser on fait : 
    git add .
    git commit -m "Déploiement de mysql"
    git push origin/loan



## Instructions

### Création d'une Machine virtuelle

Créer une machine virtuelle Linux de la Distribution Ubuntu 22.04 server 64 (1vCPU, 1GBRAM)
Créer une machine virtuelle avec un disque fixe de 30GB: 
- Créer une partition fixe swap (égale ou deux fois la taille de la RAM)
- Créer une partition pour le / (la racine)

Supprimer la machine virtuelle précédente depuis virtualbox.

Créer une machine virtuelle Linux de la Distribution Ubuntu 22.04 server 64 (1vCPU, 1GBRAM)
Créer une machine virtuelle avec un disque dynamique
Laisser Ubuntu arranger organiser votre disque

IMPORTANT : Faites une copie de la VM en l'état.


### Connectez vous sur la machine virtuelle

L'objectif est de vous connecter en console ssh depuis le terminal vSCode à la machine virtuelle.
SSH permet de vous connectez depuis votre machine hote à un serveur distant qui peut etre localisé n'importe ou.

- Allez en console sur la machine en ouvrant la console virtualbox.
- Récupérer l'addresse IP de la machine allouée par virtualBox à la VM (Virtual Machine)
 (Devinez la commande sur linux pour récupérer les adresses IP allouées à votre VM)

- Depuis votre terminal taper la commande suivante :
ssh login_linux@adresse_ip_de_la_vm


### Installez un serveur web : de facon manuelle

Votre objectif sera d'installer un serveur wordpress. Wordpress est un Content Management System (Systeme de Gestion de Contenu) CMS. Ce CMS est le plus connu et il est aussi tres puissant permettant a des utilisateurs ayant une faible experience dans le web pour faire leur site vitrine. A un site de eCommerce tres complexe.

- Suivez le tutorial suivant : https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview
- Accèder au service wordpress depuis votre navigateur web.

### Installez un serveur web sur des containers

On va cette fois-ci installer le serveur web en utilisant la containerisation.
La containerisation ce n'est pas une forme de virtualisation. C'est l'execution d'une application sous forme de service (daemon).
Nous n'avons plus de couche d'hyperviseurs mais une couche Operating system qui execute les applications sous des containeurs. Voici un petit papier de la société Red Hat que je vous conseille de lire au mois jusqu'à la partie 'machine virtuelle et containers'.

- Reprendre la sauvegarde de la VM que vous avez copié depuis VIrtualBox
- Installer docker server sur ubuntu https://docs.docker.com/engine/install/ubuntu/
- Installer mysql en lancant la commande suivante pour récupérer le container mysql voir page sur le dockerhub : https://hub.docker.com/_/mysql
    docker pull mysql
    docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag   //Voir les options

- Installer wordpress en lancant la commande suivante https://hub.docker.com/_/wordpress :
    docker pull wordpress
    docker run --name some-wordpress --network some-network -d wordpress    // Voir les options

- Accèder au service wordpress depuis votre navigateur web.

Dans cette partie il est important que vous comprenenez comment fonctionne la containerisation avec docker. Comment accéder aux services hébergés sur des containers.



### Installez un serveur web sur des containers en utilisant l'automatisation des containers

Dans cette partie nous allons utilisez un moyen d'orchestration docker-compose pour deployer des containers pré-configurés.
L'objectif est de créer votre premier script docker-compose qui va séquencer la création d'un container mysql et wordpress.
Ce script doit etre partagé depuis votre machine hote vers la machine virtuelle.

1 - Reprendre la copie de la VM et installer docker-compose sur la VM:
    https://docs.docker.com/compose/install/linux/
2 - Configuration de la VM dossier partagé (ou Shared Folder)
3 - Partagé le dossier ou se situera votre script (dans le dossier virtuallab)
4 - Créer le fichier docker-compose.yaml
5 - Développer le script