
```yml
version: '3.6'
services:
 mysql:
    build:
      context: .
      dockerfile: dockerfile_mariadb
    container_name: octopus_db
    environment:
      MARIADB_ROOT_PASSWORD: ${DB_ROOT_PASSWORD}
      MARIADB_DATABASE: octopus,vikunja,gitlab
      MARIADB_USER: ${DB_USER}
      MARIADB_PASSWORD: ${DB_USER_PASSWORD}
    volumes:
      - /D32R5/volumes/mariadb:/var/lib/mysql
    restart: unless-stopped
    networks:
      - octopus_lan

networks:
  octopus_lan:
    name: 'octopus_lan'
```

```
FROM mariadb:latest
```
