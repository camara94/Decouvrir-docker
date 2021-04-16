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

## Exécuter un conteneur docker
* <code>docker run nomImage</code>
* <code>docker run -ti nomImage</code> pour l'exécuter en mode interactif
* <code> docker ps -a</code> pour afficher les conteneurs la lancé
* [Ressource pour configurer mongodb sur mon VPS](https://www.bmc.com/blogs/mongodb-docker-container/)
  
## Exécution en mode attaché et detaché
* <code>docker run --name=mongodb --hostnamehost01 -it mong</code>
* pour verifier le nom <code>hostname</code>
* pour arrêter un conteneur <code>exit</code>
* mode d'exécution en arrière plan on ajoute l'option **-d** ou **--detach** ex: <br/><code>docker run -d -it mongo</code>
* on peut aussi balancer d'un mode en un autre avec les combinaisions suivantes: <br/> 
* on peut vérifier les log d'un conteneur en arrière plan <code>docker logs nomImage</code>
  
## Inspecter un conteneur
* on va lancer d'abord un conteneur pour pouvoir effectuer des des inspections.<br/>
<code>docker run -d -P --name=web03 --hostname=cont03 nginx</code>
* primièrement nous allons lancer la commande <code>docker inspect web03</code> 
  ![inspect un conteneur](images/docker-inspect.png)
* on peut également extraire une partie ou un attribut d'un champs avec la commande suivante: <br />
  <code>docker inspect --format='{{.state.Status}} web03</code>
  ![Docker inspect state](images/docker-inspect-state.png)

* autre par exemple:<br />
  <code>docker inspect --format='{{.NetworkSettings.IPAddres}}' web03</code>
  ![ipaddress](images/docker-inspect-networksettings.png)

* une dernière possibilité est: <br/>
  <code>docker inspect --format='{{json .State}}' web03</code>
  ![inpect state](images/docker-inspect-state2.png)

## Comment lister les conteneur docker
* pour lister les conteneurs lancés<br />
    <code>docker ps</code>
    ![docker ps](images/dockerps.png) 
* pour lister tous les conteneurs même ceux qui sont arrêtes<br />
  <code>docker ps -a</code>
  ![docker ps -a](images/dockerpsa.png)
* pour voir les n derniers conteneurs<br/>
  <code>docker ps --last 2</code>
  ![n dernier](images/ndernierconteneurs.png)

* afficher uniquement les ID des conteneurs<br/>
  <code>docker ps -q</code>
  ![dokcer ps -q](images/psq.png)
* les options de filtrage<br/>
  <code>docker ps -a --filter name=web</code> 
  ![docker ps -a --filter name=web](images/filter.png)
<code>docker ps -a --filter status=exited</code> 
  ![docker ps -a --filter name=web](images/exited.png)
* lorsqu'on essaye d'arrêter un conteneur en cours d'exécution on obtient une erreur<br/>
* <code>docker rm web03</code>
  ![erreur d'arrêt](images/erreurda.png)
* pour remedier à ce problème, on exécute cette commande<br />
  <code>docker rm -f web03</code>
  ![arrêt avec -f](images/arret.png)
* pour supprimer tous les conteneurs arrêtés<br/>
  <code>docker rm $(docker ps -aq --filter status=exited)
  ![tous les conteneurs arrêtés](images/arrets.png)
