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
        docker images # pour voir la liste des image en local
        docker rmi -f nomImage # pour supprimer une image
        docker rm -f $(docker ps -a -q) # pour supprimer également une image
    </pre>
</code>