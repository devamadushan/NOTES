#installer-Docker
	- #update
	`-sudo apt-get install ca-certificates curl`
	`-sudo install -m 0755 -d /etc/apt/keyrings`
	`-sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc`
	`-sudo chmod a+r /etc/apt/keyrings/docker.asc`
	Une fois que vous avez #crée-Docker-list vous pouvez installer les Plugin , container..
		- #update
		 `-sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`
#liens-Docker 
	- https://docs.docker.com/engine/install/ubuntu/#install-from-a-package
	- https://www.youtube.com/watch?v=9ml-cHpwdXQ
	- https://hub.docker.com/
#crée-Docker-list 
	Déplacez vous dans '/etc/apt/sources.list.d/'
		-`nano docker.list`
			`# Docker.list`
			`deb [arch=` #architecture `signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu` #Code_Name `stable`
#architecture 
	Pour trouver votre arch taper la commande suivante:
		`-dpkg --print-architecture` (ou)
		`-dpkg --version`
#Code_Name 
	pour trouver votre CodeName taper la commande suivante :
		`-cat /etc/lsb-release`
		`-sudo nano /etc/lsb-realease`
#ajouter-utilisateur-dans-docker 
	Pour ajouter l'utilisateur dans le groupe docker:
		`-sudo adduser $USER docker`

### Compose 

#installer-Docker-compose
	Pour installer docker compose il faut taper les commandes suivantes:
		-`sudo curl -SL https://github.com/docker/compose/releases/download/v2.29.6/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose`
		-`sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`
		-`sudo chmod +x /usr/local/bin/docker-compose
`
	et ensuite vous pouvez vérifier si vous avez bien installer Docker Compose
		`-docker-compose --version` 
#crée-un-fichier-yaml 
	Pour crée un fichier `.yml` on crée d'abords un Dossier avec le nom du projet
		-`mkdir nom_du_projet`
			et dans le dossier on va crée **docker-compose.yml**
				#yml 
			on pourrais aussi utiliser un fichier #env au lieu de écrire les nom d'utilisateur et les MDP en brut dans le fichier `.yml
#exécuter-yml 
	pour exécuter le fichier yml il faut être dans le Dossier du projet et taper la commande suivante:
		`-docker compose up` / `-docker compose up -d`

1. Installation 
	Ouvrez le Terminal et taper les commandes pour #installer-Docker , puis 
	#crée-Docker-list , une fois la création est terminer installer la version du Docker et tout les packages.
2. Run
	Vous pouvez taper la commande suivante pour lancer Docker:
		-sudo docker run hello-world
	Pour éviter de utiliser le mode Sudo, il faut #ajouter-utilisateur-dans-docker . 
3. Container 
	Pour voir les Containers tapez la commande :
		 -docker ps
	1. 
		[[MariaDB]] 
			Pour avoir une gestion de BDD.
		[[Portainer]]
			Portainer nous permet de visualiser tout les container. 
		[[Vikunja]]
			pour gérer les Todo list.
		[[GitLab]]
			pour gérer des étiquettes et les codes. 

4. [[Docker Compose]]
	 Compose c'est une différente façon pour installer les containers , #installer-Docker-compose puis #crée-un-fichier-yaml puis #exécuter-yml et pour arrêter :
		 `-docker compose down -v` / `-docker stop <container id>`
	Par défaut le nom du container elle aura  le nom du dossier où se trouve le fichier `.yml`