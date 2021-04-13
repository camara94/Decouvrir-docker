# Decouvrir-docker
Partez à la découverte de Docker, une solution de virtualisation permettant de faire tourner des applications dans des conteneurs indépendants. 

## Résumé du cours
Partez à la découverte de Docker, une solution de virtualisation permettant de faire tourner des applications dans des conteneurs indépendants. Dans cette formation pour administrateurs et chefs de projet, Samir Lakhdari vous fait découvrir les principes et le fonctionnement de Docker. Vous apprendrez à exécuter des conteneurs à partir d'images d'applications et vous verrez également comment créer vos propres images. Vous aborderez aussi le stockage de données dans des volumes persistants, la communication entre conteneurs, le réseau, la distribution d'images et, bien entendu, la sauvegarde. À la fin de cette formation, vous serez capable d'exécuter des conteneurs Docker avec des applications tierces ou avec vos propres applications.

# Machine Virtuelle VS Docker
![Machine Virtuelle vs Docker](images/machinevirtuelvsdocker.png)

## Architecture Docker
![architecture docker](images/architecturedocker.png)

### Moteur Docker (Engine)
![docker engine](images/docker-engine.png)
### Docker Client
![docker client](images/docker-client.png)
### Docker Image
![docker image](images/docker-image.png)
### Docker Conteneur
![docker conteneur](images/docker-conteneur.png)
### Docker Registre (Librairie d'images)
![docker registre](images/docker-registre.png)

## Appréhender le fonctionnement de Docker
![fonctionnement docker](images/architecturedocker-fonctionnement.png)

## Installer Docker
Après avoir decouvrir Docker, nous allons l'installer selon notre plateforme à travers ce lien ci-dessous: <br/> [Installer Docker](https://docs.docker.com/engine/install/)

## Quelques commande docker
<code>
    <pre>
        docker search nomImage # Pour chercher une image
        docker pull nomImage # pour telechager une image
        docker images # pour voir la liste des image en local
        docker rmi -f nomImage # pour supprimer une image
        docker rm -f $(docker ps -a -q) # pour supprimer également une image
    </pre>
</code>

## Explorer Docker Hub
Vous pouvez également explorer docker hub pour chercher des images et télécharger en local pour vos utilisations personnelles à travers ce lien ci-dessous: <br/> [Docker Hub](https://hub.docker.com)
## Appréhender la Docker
* pour afficher le manuel de la commande docker, on utilise l'option **--help**:<br/><code>docker --help | more</code>![docker help](images/dokerhelp.png)
* pour afficher l'aide une commande de context on utilise également l'option **--help**:<br/><code>docker container --help | more</code>![docker context help](images/dokercontexthelp.png)

## Le Cycle de vie d'un conteneur docker
### Le Cycle de vie de base d'un conteneur docker
![cycle de vie de base d'un conteneur](images/cycledeviedebasedunconteneur.png)
### Le Cycle de vie de avancé d'un conteneur docker
![cycle de vie de avancé d'un conteneur](images/cycledevieavancedunconteneur.png)