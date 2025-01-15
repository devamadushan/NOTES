---
tags:
  - Vikunja
  - Docker-compose
  - Dockerfile
  - Installation
  - Conteneur
---


## Docker compose
`docker-compose.yml`
```yml
version: '3.6'
services:
  vikunja:
    build:
      context: .
      dockerfile: dockerfile_vikunja   #fichier
    container_name: vikunja
    environment:
      VIKUNJA_DATABASE_HOST: ${DB_HOST}
      VIKUNJA_DATABASE_PASSWORD: ${DB_USER_PASSWORD}
      VIKUNJA_DATABASE_TYPE: mysql
      VIKUNJA_DATABASE_USER: ${DB_USER}
      VIKUNJA_DATABASE_DATABASE: ${DB}
      VIKUNJA_SERVICE_JWTSECRET: ${JWT_SECRET}
    ports:
      - "33050:3456"
    volumes:
      - /D32R5/volumes/vikunja:/app/vikunja/files
    restart: unless-stopped
    networks:
      -  octopus_lan

networks:
  octopus_lan:
    name: 'octopus_lan'
```


## Docker file
`dockerfile_mariadb`
```
ROM vikunja/vikunja:latest
WORKDIR /etc/vikunja
```

## Variable d'environnement
`.env`
```env
DB_USER = xxx
DB_USER_PASSWORD = xxx
DB = xxxx
DB_HOST = octopus_db
JWT_SECRET = xxx
```





Il est nécessaire de donner les droits en écriture au dossier qui contiendra les fichiers attachés.
Vikunja s'exécute comme utilisateur **1000** sans groupe par défaut.

Il est nécessaire de donner les droits d'écriture au dossier :

```
su
chown 1000 /D32R5/volumes/vikunja
```

