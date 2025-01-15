#yml-Vikunja-db:
	Dans : `docker-compose.yml`
```
version: '3'
services:
  vikunja:
    build:
      context: .
      dockerfile: Dockerfile-vikunja   #fichier
    container_name: vikunja
    environment:
      VIKUNJA_SERVICE_PUBLICURL: http://10.118.10.64:3060/
      VIKUNJA_DATABASE_HOST: db
      VIKUNJA_DATABASE_PASSWORD: changeme
      VIKUNJA_DATABASE_TYPE: mysql
      VIKUNJA_DATABASE_USER: vikunja
      VIKUNJA_DATABASE_DATABASE: vikunja
      VIKUNJA_SERVICE_JWTSECRET: jpppppp
    ports:
      - "3060:3456"
    volumes:
      - ./v_files:/app/vikunja/files
    depends_on:
      - db
    restart: unless-stopped

  db:
    container_name: vikunja-DB
    image: mariadb:10
    command: --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
    environment:
      MYSQL_ROOT_PASSWORD: supersecret
      MYSQL_USER: vikunja
      MYSQL_PASSWORD: changeme
      MYSQL_DATABASE: vikunja
    volumes:
      - ./v_db:/var/lib/mysql
    restart: unless-stopped
    healthcheck:
      test: ["CMD-SHELL", "mysqladmin ping -h localhost -u $$MYSQL_USER --password=$$MYSQL_PASSWORD"]
      interval: 2s
      start_period: 30s

volumes:
  v_files:
    name: vijunka_v_files
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/Vol/vikunja/files' #Sauvegarde sur la hote 
  v_db:
    name: vijunka_v_db
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/Vol/vikunja/db'  #Sauvegarde sur la hote 
```

#Dockerfile-vikunja
```
FROM vikunja/vikunja:latest
WORKDIR /etc/vikunja
```

#yml-Vikunja **Sans crée DB** 
	Dans : `docker-compose.yml`
````yml                                                                                
version: '3.6'
services:
  vikunja:
    build:
      context: .
      dockerfile: Dockerfile-vikunja   #fichier
    container_name: vikunja-test
    environment:
      VIKUNJA_SERVICE_PUBLICURL: http://10.118.10.44:3060/
      VIKUNJA_DATABASE_HOST: octopus-DB # container MariaDB qui est déja crée                                            (network octopus_lan)
      VIKUNJA_DATABASE_PASSWORD: 20072003 #mdp root de mariaDB
      VIKUNJA_DATABASE_TYPE: mysql
      VIKUNJA_DATABASE_USER: root #utilisateur de BDD (crée en avanvce)
      VIKUNJA_DATABASE_DATABASE: vikunja #BDD (crée en avance)
      VIKUNJA_SERVICE_JWTSECRET: jpppppp 
    ports:
      - "3060:3456"
    volumes:
      - ./v_files:/app/vikunja/files
    restart: unless-stopped
    networks:
      -  octopus_lan

networks:
  octopus_lan:
    name: 'octopus_lan' 


volumes:
  v_files:
    name: vijunka_v_files
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/Vol/vikunja/files' #Sauvegarde sur la hote 

````



1. Installation
	 Pour installer Vikunja dans un container ,nous avons juste crée un Dossier **Vikunja** et un fichier .`yml` dans le Dossier.Puis #exécuter-yml .
2. Client Vijunka
		 pour se rendre sur Vikunja , il faut aller sur le navigateur web 
			`-http://'adress-ip':port
3. Utilisateur 
	user : octopus
	mdp : 20072003
4. Utiliser un container MariaDB
	Pour utiliser un Server MariaDB qui existe déjà il faut crée #yml-Vikunja-db ,et avant cela il faut d'abord crée le serveur MariaDB (Container octopusDB) , un utilisateur et BDD.

