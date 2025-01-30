---
tags:
  - Docker
  - Notes
---

### Installation 
[[NOTES/Docker|Docker]]

### Gestion des Conteneurs
   
```
  docker run
```

- Cette commande sert à créer et démarrer un conteneur à partir d'une image Docker.

```
docker ps
``` 

- Affiche la liste des conteneurs actuellement en cours d'exécution.

 ```
   docker ps -a
 ```

  - Affiche la liste de tous les conteneurs, qu'ils soient en cours d'exécution ou arrêtés.
```
docker run --detach --name 'Nom du Container' --env MARIADB_ROOT_PASSWORD='MDP du Container' -p 'le port souhaité':3306 mariadb:latest

 ```
 
- Démarre un conteneur MariaDB en mode détaché, attribue un nom personnalisé, configure une variable d'environnement pour le mot de passe root et mappe un port local à celui du conteneur.

```
   docker exec -it 'Container Name' mariadb -u root -p
```
   
-  Permet d'exécuter des commandes interactives (comme se connecter à MariaDB) à l'intérieur d'un conteneur en cours d'exécution.

### Docker Compose

```
 docker-compose up
```
-  Démarre tous les services définis dans le fichier `docker-compose.yml` en mode interactif.
  
  
```
 docker-compose up -d
```

   - Démarre les services en mode détaché.
  
```
  docker-compose down -v
```
- Arrête les services et supprime les volumes associés, nettoyant complètement les ressources allouées.
      

### Gestion des Conteneurs et Images

```
  docker rm <container_id>
```
- Supprime un conteneur arrêté identifié par son `id` ou son nom.    
```
 docker image ls
```
- Affiche la liste des images disponibles localement.
```
 docker rmi <nom de l'image>
```
- Supprime une image Docker spécifiée.
```
docker exec -it <nom du container> /bin/bash
```
- Ouvre un terminal Bash interactif à l'intérieur d'un conteneur en cours d'exécution.
   
### Nettoyage et Optimisation
```
sudo docker restart <nom du container>
```
- Redémarre un conteneur spécifié.
```
docker system prune -a
```
- Supprime tous les conteneurs arrêtés, les images inutilisées et les réseaux non utilisés pour libérer de l'espace disque.
```
 docker update --cpus="2" gitlab
```
- Met à jour les ressources allouées au conteneur GitLab pour limiter son utilisation CPU à 2 cœurs.
   
### Surveillance et Diagnostic

```
 docker stats
```
- Affiche en temps réel les métriques des conteneurs en cours d'exécution (CPU, mémoire, etc.).
```
 docker inspect gitlab | grep -i cpu
```
- Fournit les informations détaillées sur la configuration CPU d'un conteneur spécifique en filtrant les résultats.
   
## GitLab

```
   gitlab-rails console
```
- Ouvre une console Ruby interactive pour effectuer des modifications ou des diagnostics avancés sur l'installation GitLab.
   
```
  gitlab-ctl reconfigure
```

  - Recharge la configuration de GitLab en fonction du fichier `gitlab.rb`, utile après des modifications de configuration.