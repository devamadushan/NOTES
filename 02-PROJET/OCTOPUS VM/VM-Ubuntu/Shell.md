	Docker.sh
````sh
clear

sudo apt update

sudo apt upgrade

sudo apt-get install ca-certificates curl

sudo install -m 0755 -d /etc/apt/keyrings

sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc

  
  
  

archi=$(dpkg --print-architecture)

  

code_name=$(lsb_release -c | awk '{print $2}')

  
  

touch /etc/apt/sources.list.d/docker.list

echo deb [arch=$archi signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $code_name stable | sudo tee -a /etc/apt/sources.list.d/docker.list

sudo adduser $USER docker

  

sudo apt update

sudo apt upgrade

  
  

sudo curl -SL https://github.com/docker/compose/releases/download/v2.29.6/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

  
  

docker-compose --version

  

sudo mkdir -p /Docker/portainer

sudo mkdir -p /Docker/mariaDB

sudo mkdir -p /Docker/vikunja

  
  

touch /Docker/portainer/docker-compose.yml

touch /Docker/mariaDB/docker-compose.yml

touch /Docker/mariaDB/Dockerfile-mariaDB

touch /Docker/vikunja/docker-compose.yml

touch /Docker/vikunja/Dockerfile-vikunja

  
  

####______________________________PORTAINER__________________________________####

  
  

cat << EOF | sudo tee /Docker/portainer/docker-compose.yml

version: '3.8'

  

services:

portainer:

image: portainer/portainer-ce

container_name : Portainer

ports:

- "9001:9000"

volumes:

- /var/run/docker.sock:/var/run/docker.sock

- /volumes/portainer:/data

restart: always

EOF

  
  

####_______________________________MARIA-DB________________________________####

  
  

cat << EOF | sudo tee /Docker/mariaDB/docker-compose.yml

version: '3.6'

services:

mysql:

build:

context: .

dockerfile: Dockerfile-mariaDB #fichier

container_name: octopus-DB

environment:

MARIADB_ROOT_PASSWORD: 20072003

MARIADB_DATABASE: octopus

MARIADB_USER: octopus

MARIADB_PASSWORD: 20072003

ports:

- "33060:3306"

volumes:

- /volumes/mariadb:/var/lib/mysql

restart: unless-stopped

networks:

- octopus_lan

  

networks:

octopus_lan:

name: 'octopus_lan'

  

volumes:

/volumes/mariadb:

name: octopusDB_v_files

driver: local

driver_opts:

type: 'none'

o: 'bind'

device: '/Vol/octopus_DB/db' #Sauvegarde sur la hote

EOF

  
  

echo "FROM mariadb:latest" | sudo tee -a /Docker/mariaDB/Dockerfile-mariaDB

  
  
  
  

####________________________________Vikunja_________________________________####

  

cat << EOF | sudo tee /Docker/vikunja/docker-compose.yml

version: '3.6'

services:

vikunja:

build:

context: .

dockerfile: Dockerfile-vikunja #fichier

container_name: vikunja-test

environment:

VIKUNJA_SERVICE_PUBLICURL: http://localhost:3060/

VIKUNJA_DATABASE_HOST: octopus-DB

VIKUNJA_DATABASE_PASSWORD: 20072003

VIKUNJA_DATABASE_TYPE: mysql

VIKUNJA_DATABASE_USER: octopus

VIKUNJA_DATABASE_DATABASE: octopus

VIKUNJA_SERVICE_JWTSECRET: jpppppp

ports:

- "3060:3456"

volumes:

- /volumes/vikunja :/app/vikunja/files

restart: unless-stopped

networks:

- octopus_lan

  

networks:

octopus_lan:

name: 'octopus_lan'

  
  

volumes:

/volumes/vikunja:

name: vikunja

driver: local

driver_opts:

type: 'none'

o: 'bind'

device: '/Vol/vikunja/files' #Sauvegarde sur la hote

  

EOF

  
  

sudo tee -a /Docker/vikunja/Dockerfile-vikunja << EOF

FROM vikunja/vikunja:latest

WORKDIR /etc/vikunja

EOF

  

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

  
  

for dir in /Docker/portainer /Docker/mariaDB /Docker/vikunja; do

(cd "$dir" && sudo docker-compose up -d)

done

  
  
  

echo "création de container Portainer dans /Docker/portainer"

echo "création de container MariaDB dans /Docker/mariadb"

echo "création de container vikunja dans /Docker/vikunja"
````