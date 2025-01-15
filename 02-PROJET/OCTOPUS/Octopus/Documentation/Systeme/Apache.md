---
tags:
  - Apache
  - Conteneur
  - Docker-compose
  - octopus_web
---
## octopus_web

## Docker file
`dockerfile_octopus_web`
```
FROM httpd:latest
```

## Docker compose
`docker-compose.yml`
```yml                                                               
services:
  apache:
    build:
      context: .
      dockerfile: dockerfile_octopus_web # httpd:latest
    container_name: octopus_web
    ports:
      - "80:80"
    volumes:
      - ./conf:/usr/local/apache2/conf
      - /D32R5/volumes/octopus_web/sites:/usr/local/apache2/htdocs
      - /D32R5/volumes/octopus_web/logs:/usr/local/apache2/logs
      - ./certs:/usr/local/apache2/certs
    networks:
      - octopus_lan
    restart: unless-stopped

networks:
  octopus_lan:
    name: 'octopus_lan'

```


## Bugs
 2024/11/27
- **Problème rencontré** : Lors de l'installation du conteneur, il est impossible de lancer Apache.
- **Cause** :
    -  Absence de fichier de configuration Apache dans le volume monté.
    -  Sur le conteneur, un fichier de configuration par défaut est présent. Cependant, lorsque le volume pour la configuration est monté, le fichier de configuration est absent, ce qui provoque une erreur au démarrage du conteneur.
- **Solution** : Copier manuellement le fichier de configuration par défaut présent dans le conteneur (`/usr/local/apache2/conf`) et le placer dans le répertoire monté sur le disque local (` ./conf`).