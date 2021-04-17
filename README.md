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
  <code>docker rm $(docker ps -aq --filter status=exited)</code>
  ![tous les conteneurs arrêtés](images/arrets.png)
## Comprendre une image docker
### C'est quoi une couche docker ?
![comprendre une image](images/couche.png)
### Qu'est ce qu'une image docker 
Une image est constituée de un plusieurs couche docker
#### Comment créer une image
![créer une image](images/creeruneimage.png)
#### Espace de nommage
![nommage](images/espacenommage.png)

## Comment créer une image à partir d'un conteneur docker
* <code>docker run -it --name=mycentos centos</code>
* parfaut la commande <code>wget</code> n'existe pas sur centos
  ![myfirstimage](images/myfirstimage.png)
* on va installer **wget** dans centos
* <code>yum install wget</code>
  ![yum install](images/yuminstall.png)
* on va tester **wget** <code>wget</code>, puis on l'arrêter et enfin nous allons tester <code>docker ps -a</code>
  ![qlq cmd](images/qlqcmd.png)
* on peut visualiser les différences
  <code>docker diff mycentos</code>
  ![diff](images/diffwget.png)
  > pour dire que dans le dossier **/bin** nous avons installer **wget**<br/>
  > A sigifie **Ajout** <br />
  > C sigifie **Change** <br />
  > D signifie **Delete**

### Comment enrégister sur notre depôt
<code>docker commit mycentos ldamaro98/mycentos:1.0</code>
## Générer des volumes docker
* Volumes nommés<br />
  <code>docker volume create --name=vol1</code>
* Pour afficher la liste des volumes docker<br/>
  <code>docker volume ls</code>
* Pour monter un volume<br />
   <code>docker run -it -v vol1:/www/html mycentos</code>
* Pour inspeter le volume<br/>
  <code>docker volume inspect vol1</code>
* Pour supprimer un volume<br/>
  <code>docker volume rm -f vol1</code>
* Pour créer un anonyme, on le crée lors de lancement d'un conteneur<br/>
  <code>docker run -v /var/www/html mycentos</code>
* Pour supprimer un volume anonyme, lors de la suppression d'une image<br />
  <code>docker rm -v idImage</code>
## Aborder les volumes d'hôte
* nous allons d'abord lancer un serveur **nginx**<br/>
  <code>docker run -d --name=nginx nginx</code>
* Pour se connecter à un conteneur docker<br/>
  <code>docker exec -it nginx</code>
* Pour afficher le contenu du ficher de configuration<br/>
  <code>cat /etc/nginx/nginx.conf</code>
  ![conf](images/nginxconf.png)
* Pour quitter(se deconnecter de **nginx**)<br>
  <code>exit</code>
* Pour arrêter le conteneur<br/>
  <code>docker stop nginx </code>
* Pour récupérer un du conteneur vers un fichier local<br/>
  <code>mkdir nginxconf && cd nginxconf</code><br/>
  <code>docker cp nginx:/etc/nginx/nginx.conf .</code>
  ![ngix conf](images/cpnginx.png)
* Pour monter le fichier dans notre conteneur<br/>
  <code>docker run -d --name=nginx2 -v /home/user1/nginx/nginx.conf:/etc/nginx/nginx.conf</code>
* Se connecter au connecter et vérifier <br/>
  <code>docker exec -it nginx2 bash</code><br/>
  <code>cat /etc/nginx/nginx.conf</code>
  ![verifi](images/verifnginx.png)

## Découvrir le modèle réseau
![modele reseau](images/reseaubridge.png)