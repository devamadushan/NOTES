
## Installations
Pour Installer **Docker** il faut d'abord passer en mode #su et faire un #update puis les commandes suivantes :
- `apt-get install ca-certificates curl`
- `install -m 0755 -d /etc/apt/keyrings`
- `curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc`
- `chmod a+r /etc/apt/keyrings/docker.asc`
déplacez vous dans `/etc/apt/sources.list.d/`
	crée un fichier `docker.list`
		- `nano docker.list`
	trouver **l'architecture**:
		- `dpkg --print-architecture`
	trouver **Code_Name**:
		- `cat /etc/os-release`  
	écrire dans ce fichier :
````
deb [arch=<architecture> signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian <Code_Name> stable
````
faire un #update 
	- `apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`
Pour installer ***Docker compose*** :
	- `curl -SL https://github.com/docker/compose/releases/download/v2.29.6/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose`
	- `ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`
	- `chmod +x /usr/local/bin/docker-compose`
Pour vérifier si vous avez bien installer **Docker Compose**
	- `docker-compose --version`

