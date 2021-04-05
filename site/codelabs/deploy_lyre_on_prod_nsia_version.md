author: LJ Group
summary: Deployer Lyre en Production - NSIA Version 
id: deployer-lyre-production
categories: lyre
environments: Web
status: Published


# Comment déployer lyre en production (Version NSIA)


## Première Etape : Cloner le projet 
Duration: 0:01:00

La première étape lors du déploiement de lyre est de cloner le projet. Pour le faire, tapez la commande suivante en spécifiant la branche qui vous convient. 

![alt-text-here](assets/deployer-lyre-version-nsia/1.png)
 
## Deuxième étape : Copier les clés et certificats
Duration: 0:01:00

Après avoir procédé au clonage de votre projet, il est recommandé de copier les clés et certificats dans le dossier lyredbb/php.
Entrez les commandes suivantes :

![alt-text-here](assets/deployer-lyre-version-nsia/2.png)

## Troisième étape : Configuration Docker
Duration: 0:01:00
Cette étape nécessite en premier lieu des mises à jour de votre fichier DockerFile.
Pour afficher ce fichier, tapez la commande: vi DockerFile.
Ensuite, modifiez le comme indiqué sur l'image suivante :

![alt-text-here](assets/deployer-lyre-version-nsia/dockerfile.png)

## Quatrième étape :  Définir le fichier d'environnement de production
Duration: 0:01:00

Il est recommandé de copier votre fichier d'environnement en tant fichier d'environnement de production. 
Tapez les commandes suivantes:

![alt-text-here](assets/deployer-lyre-version-nsia/4.png)


## Cinquième étape : Construire l'image docker
Duration: 0:01:00

A cette étape , vous devez construire l'image de déploiement docker avec tag_image pour le nom de l'image.

Tapez la commande suivante:

![alt-text-here](assets/deployer-lyre-version-nsia/5.png)

## Sixième étape : Lancement de votre nouveau conteneur
Duration: 0:01:00

Pour lancer votre nouveau conteneur, il est recommandé d'afficher tous les conteneurs en cours, afin de récupérer l'id de l'ancien conteneur avec la commande suivante.

![alt-text-here](assets/deployer-lyre-version-nsia/6.png)

Ensuite,arrêtez le conteneur dont vous avez récupéré l'id.

![alt-text-here](assets/deployer-lyre-version-nsia/7.png)

Pour lancer votre nouveau conteneur docker, entrez la commande suite : 

docker run --restart=always --name lyrensia  -p 443:443 --link nom_du_conteneur_de_la_BD:mysql -d tag_image


## Options de commandes
Duration: 0:01:00

Il est important de connaitre des options de commandes qui demeurent importantes pour le déploiement de lyre.

- **--restart=always** : Toujours redémarrer le conteneur au démarrage du poste
- **--name** : Nom donné au conteneur
- **-p 443:443** : Exposition d'un numéro de port. Le conteneur pourra être contacté au port 443 sur le port 443 de la machine hôte (<port_hote>:<port_conteneur>)
- **--link** : Le conteneur de la base de donnée sera identifé comme "mysql" dans le conteneur en cours de création
- **-d** : Nom de l'image docker

## Informations utiles
Duration: 0:01:00

Pour ouvrir un shell dans votre conteneur,vous pouvez utiliser la commande suivante :

 ![alt-text-here](assets/deployer-lyre-version-nsia/shell.png)

 Pour visualiser les logs d'un conteneur en temps réel, tapez la commande ci-dessous.

 ![alt-text-here](assets/deployer-lyre-version-nsia/8.png)

 # Contact Us
 We assure you that you will not find any issue with this How to deploy lyre on nsia prod version tutorial. But if there is any mistake or error, please contact us.
[LJ Group - Our site](https://www.ljgroup.fr)
