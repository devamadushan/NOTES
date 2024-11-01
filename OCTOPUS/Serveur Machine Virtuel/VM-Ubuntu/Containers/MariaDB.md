### Compose : 

#yml-MariaDB     
	Dans : `docker-compose.yml`
```
version: '3'
services:
 mysql:
    build:
      context: .
      dockerfile: Dockerfile-mariaDB   #fichier
    container_name: octopus-DB
    environment:
      MARIADB_ROOT_PASSWORD: 20072003
      MARIADB_DATABASE: octopus
      MARIADB_USER: octopus
      MARIADB_PASSWORD: 20072003
    ports:
      - "33060:3306"
    volumes:
      - ./v_mariadb:/var/lib/mysql
    restart: unless-stopped
    networks:
      - mariadb_net

networks:
  mariadb_net:
    name: 'mariadb_net'

volumes:
  v_mariadb:
    name: octopusDB_v_files
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/Vol/octopus_DB/db' #Sauvegarde sur la hote 


```

#Dockerfile-mariaDB                                                                          
````
FROM mariadb:latest
````
#mariaDB
	1. Installation
		`sudo apt-get install mariadb-server mariadb-client`
#connecter-sur-le-container (MariaDB)
	- `sudo docker exec -it <nom du container> bash`
#bind-adress 
	- déplacer dans `/etc/mysql/mariadb.conf.d/`
	- modifier `nano -server.cnf`
	- `[mysqld] bind-address = 127.0.0.1`
	
### Autres Méthodes : 

#server-MariaDB
	Pour crée un container MariaDB il faut taper la commande suivante:
		-docker run --detach --name **'Nom du Container'** --env MARIADB_ROOT_PASSWORD=**'MDP du Container'** -p **'le port souhaité'** :3306 mariadb:latest 
#communiquer-avec-le-serveur-MariaDB  
	Pour se connecter avec un root : 
		-docker exec -it **'nom du container'** mariadb -u root -p
	On peut aussi crée un utilisateur qui peut étre utiliser par une machine ou plusieur machine:
		Une fois que on est connecter avec le root , on écrit un requête [[SQL]] :
			-CREATE USER 'User Name'@' #ip' IDENTIFIED BY 'MDP';
			-GRANT ALL PRIVILEGES ON **BDD**.* TO 'utilisateur'@' #ip';
	Pour se connecter au serveur avec un autre utilisateur que root sur une autre machine , il faut d'abord installer #mariaDB-client et taper la commande suivante:
		-mariadb -h  **'adress Ip du #server-MariaDB'**  -P **'port'** -u **'nom d'utilisateur'** -p


1. Installation 
	1. Compose :
		1. Pour installer le Container MariaDB sur Docker il faut crée un répertoire **MariaDb ou octopus DB** et créé le fichier #yml-MariaDB . puis #exécuter-yml 
2. Configuration
	1. pour bloquer la communication entre la BDD et une machine qui n'est pas dans le mémé réseaux 
		- il faut se #connecter-sur-le-container
		- ajouter #bind-adress
		- redémarrer Mariadb  `sudo docker restart <container>`
		-en utilisant Bind le Server sera accessible uniquement pour le Localhost donc si on veut faire utiliser le Server par une autre machine (Vikunja , GitLab) on ne pourra pas. 
		

Une fois que on a crée le #server-MariaDB on essaie de #communiquer-avec-le-serveur-MariaDB  sois en localhost ou depuis une autre machine.


