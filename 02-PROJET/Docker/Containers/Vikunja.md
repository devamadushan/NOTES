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



```
ROM vikunja/vikunja:latest
WORKDIR /etc/vikunja
```

```env
DB_USER = xxx
DB_USER_PASSWORD = xxx
DB = xxxx
DB_HOST = octopus_db
JWT_SECRET = xxx

```